```
MLFlow
```

Base type which defines location and version for MLFlow API service.

# Fields

  * `apiroot::String`: API root URL, e.g. `http://localhost:5000/api`
  * `apiversion::Union{Integer, AbstractFloat}`: used API version, e.g. `2.0`
  * `headers::Dict`: HTTP headers to be provided with the REST API requests.
  * `username::Union{Nothing, String}`: username for basic authentication.
  * `password::Union{Nothing, String}`: password for basic authentication.

!!! warning
    You cannot provide an `Authorization` header when an `username` and `password` are provided. An error will be thrown in that case.


!!! note
      * If `MLFLOW_TRACKING_URI` is set, the provided `apiroot` will be ignored.
      * If `MLFLOW_TRACKING_USERNAME` is set, the provided `username` will be ignored.
      * If `MLFLOW_TRACKING_PASSWORD` is set, the provided `password` will be ignored.

    These indications will be displayed as warnings.


# Examples

```@example
mlf = MLFlow()
```

```@example
remote_url="https://<your-server>.cloud.databricks.com"; # address of your remote server
mlf = MLFlow(remote_url, headers=Dict("Authorization" => "Bearer <your-secret-token>"))
```
