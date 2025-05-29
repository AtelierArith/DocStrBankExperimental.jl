Reconstructed Tracker Pulse

  * Author: Wenxing Fang, IHEP

# Fields

  * `cellID::UInt64`: cell id.
  * `time::Float32`: time [ns].
  * `charge::Float32`: charge [fC].
  * `quality::Int16`: quality.
  * `covMatrix::SVector{3,Float32}`: lower triangle covariance matrix of the charge(c) and time(t) measurements.

# Relations

  * `timeSeries::TimeSeries`: Optionally, the timeSeries that has been used to create the pulse can be stored with the pulse.
