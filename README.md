# dify-coolify

This configuration uses the default settings for Qdrant and OpenDAL FS.

## Deployment on Coolify

Follow these steps to deploy to Coolify. These instructions include workarounds for Coolify-specific issues.

1.  **Import `docker-compose.yaml`**: Start by importing the `docker-compose.yaml` file into your Coolify project.

2.  **Clear Application Directory**: After importing, navigate to `/data/coolify/applications/<Application ID>/` on your server and delete all files and folders within it.
    > **Note**: Replace `<Application ID>` with the actual ID of your application in Coolify.

3.  **Set Environment Variables**:
    *   Go to the "Environment Variables" tab in your Coolify project settings.
    *   Click the `+Add` button to create two new variables:
        *   `EXPOSE_NGINX_PORT`
        *   `EXPOSE_NGINX_SSL_PORT`
    *   Assign a unique, non-conflicting port number to each.

4.  **Preserve Repository**:
    *   Go to the "General" tab.
    *   Enable the "Preserve Repository During Deployment" option.

5.  **Deploy**: Click the "Deploy" button to start the deployment process.

6.  **Troubleshooting**:
    *   Check the "Logs" tab for any errors.
    *   If you encounter a migration error, click the "Stop" button to halt the application, and then click "Deploy" again to restart the process.
    *   When enabling **Connect To Predefined Network**, no manual changes are required—each container now forces Docker's embedded DNS resolver (`127.0.0.11`), so `nginx` keeps resolving `web`/`api` internally and 502 responses on `${EXPOSE_NGINX_PORT}` are avoided.
