

# This stage builds the application
FROM microsoft/dotnet:2.1-sdk AS build
COPY . src
WORKDIR src
RUN dotnet restore
RUN dotnet publish -c release/netcoreapp2.1/publish

# This stages uses the output from the build
FROM microsoft/dotnet:2.1-aspnetcore-runtime
COPY --from=builder src/bin/release/netcoreapp2.1/publish app
WORKDIR app
ENV ASPNETCORE_URLS http://*:80
EXPOSE 80
ENTRYPOINT ["dotnet", "netcore21test.dll"]