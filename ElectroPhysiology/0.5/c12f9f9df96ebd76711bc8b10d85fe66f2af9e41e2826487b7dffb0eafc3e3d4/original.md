```
readABF(::Type{T}, FORMAT::Type, abf_data::Union{String,Vector{UInt8}};
    trials::Union{Int64,Vector{Int64}}=-1,
    channels::Union{Int64, String, Vector{String}, Nothing}=nothing,
    average_trials::Bool=false,
    stimulus_name::Union{String, Vector{String}, Nothing}=nothing,
    stimulus_threshold::T=2.5,
    warn_bad_channel=false,
    flatten_episodic::Bool=false,
    time_unit=:s
) where {T<:Real}
```

Read and parse Axon Binary Format (ABF) files, returning an Experiment object containing the electrophysiology data and associated metadata.

# Arguments

  * `T`: The numeric type for the data (e.g., Float32, Float64)
  * `FORMAT`: The format type of the experiment
  * `abf_data`: Either a file path to the ABF file or raw ABF data as a byte vector

# Optional Arguments

  * `trials`: Trial selection

      * `-1`: All trials (default)
      * `Int64`: Single trial
      * `Vector{Int64}`: Multiple specific trials
  * `channels`: Channel selection

      * `nothing`: All channels (default)
      * `Int64`: Single channel by index
      * `String`: Single channel by name
      * `Vector{String}`: Multiple channels by name
  * `average_trials`: Whether to average across trials (default: false)
  * `stimulus_name`: Name of stimulus channel(s)

      * `nothing`: No stimulus (default)
      * `String`: Single stimulus channel
      * `Vector{String}`: Multiple stimulus channels
  * `stimulus_threshold`: Threshold for detecting digital stimulus events (default: 2.5)
  * `warn_bad_channel`: Whether to warn about invalid channels (default: false)
  * `flatten_episodic`: Whether to flatten episodic data into continuous data (default: false)
  * `time_unit`: Time unit for the data

      * `:s`: Seconds (default)
      * `:ms`: Milliseconds

# Returns

  * An Experiment object containing:

      * Raw data array
      * Time vector
      * Channel names and units
      * Stimulus protocol (if specified)
      * Original ABF metadata in HeaderDict

# Channel Naming Conventions

1. ADC channels: Use exact names from recording (e.g., "Vm_prime", "IN 7")
2. Analog channels: "A1", "A2", etc. or "Analog 1", "Analog 2", etc.
3. Digital channels: "D1", "D2", etc. or "Digital 1", "Digital 2", etc.

# Examples

```julia
# Basic usage - read all channels and trials
exp = readABF(Float32, "path/to/file.abf")

# Read specific channels and average trials
exp = readABF(Float32, "path/to/file.abf",
    channels=["Vm_prime", "IN 7"],
    average_trials=true)

# Read with stimulus extraction
exp = readABF(Float32, "path/to/file.abf",
    stimulus_name="Digital 1",
    stimulus_threshold=2.5)

# Read specific trials and flatten episodic data
exp = readABF(Float32, "path/to/file.abf",
    trials=1:5,
    flatten_episodic=true)

# Read with time in milliseconds
exp = readABF(Float32, "path/to/file.abf",
    time_unit=:ms)
```

See also: [`parseABF`](@ref), [`getWaveform`](@ref), [`extractStimulus`](@ref)
