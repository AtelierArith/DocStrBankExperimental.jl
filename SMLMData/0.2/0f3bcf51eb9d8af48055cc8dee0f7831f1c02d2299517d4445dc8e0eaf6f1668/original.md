```
BasicSMLD(emitters::Vector{E}, camera::AbstractCamera,
          n_frames::Int, n_datasets::Int,
          metadata::Dict{String,Any}=Dict{String,Any}()) where E<:AbstractEmitter
```

Construct a BasicSMLD from a vector of emitters and required metadata.

# Arguments

  * `emitters::Vector{E}`: Vector of localized emitters
  * `camera::AbstractCamera`: Camera used for acquisition
  * `n_frames::Int`: Total number of frames in acquisition
  * `n_datasets::Int`: Number of datasets in acquisition
  * `metadata::Dict{String,Any}=Dict{String,Any}()`: Optional additional information

The numeric type T is inferred from the camera's pixel*edges*x type.

# Example

```julia
# Create with minimal metadata
data = BasicSMLD(emitters, camera, 10, 1)

# Create with additional metadata
data = BasicSMLD(emitters, camera, 10, 1, Dict(
    "exposure_time" => 0.1,
    "timestamp" => now()
))
```
