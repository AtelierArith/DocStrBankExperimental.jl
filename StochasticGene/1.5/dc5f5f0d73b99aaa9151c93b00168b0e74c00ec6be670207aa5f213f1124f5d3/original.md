```
datapdf(data)
```

Returns the normalized RNA histogram data as one vector.

# Arguments

  * `data::AbstractRNAData{Array{Float64,1}}`: RNA histogram data.
  * `data::RNAOnOffData`: RNA On/Off data.
  * `data::AbstractTraceHistogramData`: Trace histogram data.
  * `data::AbstractRNAData{Array{Array,1}}`: RNA histogram data with nested arrays.
  * `data::RNADwellTimeData`: RNA dwell time data.

# Description

This function normalizes the RNA histogram data and returns it as one vector. It supports various types of RNA data, including RNA histogram data, RNA On/Off data, trace histogram data, and RNA dwell time data.

# Methods

  * `datapdf(data::AbstractRNAData{Array{Float64,1}})`: Normalizes and returns RNA histogram data.
  * `datapdf(data::RNAOnOffData)`: Normalizes and returns RNA On/Off data.
  * `datapdf(data::AbstractTraceHistogramData)`: Normalizes and returns trace histogram data.
  * `datapdf(data::AbstractRNAData{Array{Array,1}})`: Normalizes and returns RNA histogram data with nested arrays.
  * `datapdf(data::RNADwellTimeData)`: Normalizes and returns RNA dwell time data.

# Returns

  * `Vector{Float64}`: Normalized RNA histogram data as one vector.
