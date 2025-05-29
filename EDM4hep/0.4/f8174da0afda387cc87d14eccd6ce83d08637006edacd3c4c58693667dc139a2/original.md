Calibrated Detector Data

  * Author: Wenxing Fang, IHEP

# Fields

  * `cellID::UInt64`: cell id.
  * `time::Float32`: begin time [ns].
  * `interval::Float32`: interval of each sampling [ns].
  * `amplitude::PVector{Float32}`: calibrated detector data.

# Methods

  * `setAmplitude(object::TimeSeries, v::AbstractVector{Float32})`: assign a set of values to the `amplitude` vector member
