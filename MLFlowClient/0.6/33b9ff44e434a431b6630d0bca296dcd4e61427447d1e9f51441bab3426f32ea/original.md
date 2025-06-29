```
ModelVersion
```

# Fields

  * `name::String`: Unique name of the model.
  * `version::String`: Model’s version number.
  * `creation_timestamp::Int64`: Timestamp recorded when this model_version was created.
  * `last_updated_timestamp::Int64`: Timestamp recorded when metadata for this model_version   was last updated.
  * `user_id::Union{String, Nothing}`: User that created this model_version.
  * `current_stage::String`: Current stage for this model_version.
  * `description::String`: Description of this model_version.
  * `source::String`: URI indicating the location of the source model artifacts, used when   creating model_version.
  * `run_id::String`: MLflow run ID used when creating model_version, if source was generated   by an experiment run stored in MLflow tracking server.
  * `status::ModelVersionStatus`: Current status of model_version.
  * `status_message::String`: Details on current status, if it is pending or failed.
  * `tags::Array{Tag}`: Additional metadata key-value pairs.
  * `run_link::String`: Direct link to the run that generated this version. This field is set   at model version creation time only for model versions whose source run is from a   tracking server that is different from the registry server.
  * `aliases::Array{String}`: Aliases pointing to this model_version.
