```
BasicSMLD{T,E<:AbstractEmitter} <: SMLD
```

Basic container for single molecule localization data.

# Fields

  * `emitters::Vector{E}`: Vector of localized emitters
  * `camera::AbstractCamera`: Camera used for acquisition
  * `n_frames::Int`: Total number of frames in acquisition
  * `n_datasets::Int`: Number of datasets in the acquisition
  * `metadata::Dict{String,Any}`: Additional dataset information

# Type Parameters

  * `T`: Numeric type for coordinates (typically Float64)
  * `E`: Concrete emitter type

# Example

```julia
# Create camera
cam = IdealCamera(1:512, 1:512, 0.1)

# Create some emitters
emitters = [
    Emitter2DFit{Float64}(1.0, 1.0, 1000.0, 10.0, 0.01, 0.01, 50.0, 2.0; frame=1),
    Emitter2DFit{Float64}(5.0, 5.0, 1200.0, 12.0, 0.01, 0.01, 60.0, 2.0; frame=2)
]

# Create metadata
metadata = Dict{String,Any}(
    "exposure_time" => 0.1,
    "timestamp" => now(),
    "sample" => "Test Sample"
)

# Create SMLD object
data = BasicSMLD(emitters, cam, 2, 1, metadata)
```
