```
RunInfo
```

Metadata of a single run.

# Fields

  * `run_id::String`: Unique identifier for the run.
  * `run_name::String`: The name of the run.
  * `experiment_id::String`: The experiment ID.
  * `status::RunStatus`: Current status of the run.
  * `start_time::Int64`: Unix timestamp of when the run started in milliseconds.
  * `end_time::Int64`: Unix timestamp of when the run ended in milliseconds.
  * `artifact_uri::String`: URI of the directory where artifacts should be uploaded. This can   be a local path (starting with “/”), or a distributed file system (DFS) path,   like s3://bucket/directory or dbfs:/my/directory. If not set, the local ./mlruns   directory is chosen.
  * `lifecycle_stage::String`: Current life cycle stage of the experiment: "active" or   "deleted".
