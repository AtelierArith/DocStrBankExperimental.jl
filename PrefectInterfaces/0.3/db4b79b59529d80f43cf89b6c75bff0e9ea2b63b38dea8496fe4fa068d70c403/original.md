```
ls(; type="block", api::PrefectAPI = PrefectAPI())
```

Calls the Prefect server and returns a list of all defined blocks as Vector{String}. Default is to list all blocks, later implementation could include "flows", "deployments", "work-pool" etc. See `PrefectAPI` docs for details about authentication if needed.

# Examples:

```julia
julia> ENV["PREFECT_API_URL"] = "http://127.0.0.1:4300/api";

julia> ls()
11-element Vector{Any}:
 "aws-credentials/subdivisions"
 "docker-container/lamneth"
 "github/dev"
 "github/main"
 "local-file-system/willowdata"
 "process/red-barchetta"
 "s3/necromancer"
 "s3-bucket/willowdata"
 "secret/necromancer"
 "slack-webhook/bytor-alert"
 "string/environment"
```
