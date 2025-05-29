```
Experiment
```

# Fields

  * `experiment_id::Integer`: Unique identifier for the experiment.
  * `name::String`: Human readable name that identifies the experiment.
  * `artifact_location::String`: Location where artifacts for the experiment are stored.
  * `lifecycle_stage::String`: Current life cycle stage of the experiment: “active” or   “deleted”. Deleted experiments are not returned by APIs.
  * `last_update_time::Int64`: Last update time.
  * `creation_time::Int64`: Creation time.
  * `tags::Array{Tag}`: Additional metadata key-value pairs.
