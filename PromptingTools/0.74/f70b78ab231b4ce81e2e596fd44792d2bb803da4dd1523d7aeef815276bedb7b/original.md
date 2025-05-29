```
DataMessage
```

A message type for AI-generated data-based responses, ie, different `content` than text.  Returned by `aiextract`, and `aiextract` functions.

# Fields

  * `content::Union{AbstractString, Nothing}`: The content of the message.
  * `status::Union{Int, Nothing}`: The status of the message from the API.
  * `tokens::Tuple{Int, Int}`: The number of tokens used (prompt,completion).
  * `elapsed::Float64`: The time taken to generate the response in seconds.
  * `cost::Union{Nothing, Float64}`: The cost of the API call (calculated with information from `MODEL_REGISTRY`).
  * `log_prob::Union{Nothing, Float64}`: The log probability of the response.
  * `extras::Union{Nothing, Dict{Symbol, Any}}`: A dictionary for additional metadata that is not part of the key message fields. Try to limit to a small number of items and singletons to be serializable.
  * `finish_reason::Union{Nothing, String}`: The reason the response was finished.
  * `run_id::Union{Nothing, Int}`: The unique ID of the run.
  * `sample_id::Union{Nothing, Int}`: The unique ID of the sample (if multiple samples are generated, they will all have the same `run_id`).
