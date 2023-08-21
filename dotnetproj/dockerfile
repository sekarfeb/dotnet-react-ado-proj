FROM mcr.microsoft.com/dotnet/sdk:6.0 as build
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
WORKDIR /app
RUN dotnet build
RUN dotnet publish -c Release -o /app/out

FROM mcr.microsoft.com/dotnet/aspnet:6.0 as runtime
WORKDIR /app
COPY --from=build /app/out ./
ENTRYPOINT ["dotnet", "Helloworldapp.web.dll"]