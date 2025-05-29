```
ProgressParams(; progress_token::ProgressToken, progress::Float64,
             total::Union{Float64,Nothing}=nothing) <: RequestParams
```

Parameters for progress notifications during long-running operations.

# Fields

  * `progress_token::ProgressToken`: Token identifying the operation being reported on
  * `progress::Float64`: Current progress value
  * `total::Union{Float64,Nothing}`: Optional total expected value
