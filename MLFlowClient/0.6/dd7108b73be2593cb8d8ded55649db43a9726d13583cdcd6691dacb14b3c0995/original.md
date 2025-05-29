```
RegisteredModel
```

# Fields

  * `name::String`: Unique name for the model.
  * `creation_timestamp::Int64`: Timestamp recorded when this RegisteredModel was created.
  * `last_updated_timestamp::Int64`: Timestamp recorded when metadata for this   RegisteredModel was last updated.
  * `user_id::Union{String, Nothing}`: User that created this RegisteredModel.
  * `description::Union{String, Nothing}`: Description of this RegisteredModel.
  * `latest_versions::Array{ModelVersion}`: Collection of latest model versions for each   stage. Only contains models with current READY status.
  * `tags::Array{Tag}`: Additional metadata key-value pairs.
  * `aliases::Array{RegisteredModelAlias}`: Aliases pointing to model versions associated   with this RegisteredModel.
