#Etap 1 - Build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS Build
WORKDIR /src

#Etap 2 - kopiujemy csproj
COPY *. csproj . /
RUN dotnet restore

#Kopiujemy resztę plików
COPY . ./
RUN dotnet publish -c Realse -k /app/publish

#Runtime
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS final
WORKDIR /app

COPY --from=Build app/publish .

ENV ASPNETCORE_URLS=http://+:800
EXPOSE 8080

ENTRYPOINT [ "dotnet", "Api.dll" ]