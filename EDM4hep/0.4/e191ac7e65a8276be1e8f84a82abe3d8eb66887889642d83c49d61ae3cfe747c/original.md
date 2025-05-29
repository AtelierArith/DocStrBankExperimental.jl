Raw data of a detector readout

  * Author: F.Gaede, DESY

# Fields

  * `cellID::UInt64`: detector specific cell id.
  * `quality::Int32`: quality flag for the hit.
  * `time::Float32`: time of the hit [ns].
  * `charge::Float32`: integrated charge of the hit [fC].
  * `interval::Float32`: interval of each sampling [ns].
  * `adcCounts::PVector{Int32}`: raw data (32-bit) word at i.

# Methods

  * `setAdcCounts(object::RawTimeSeries, v::AbstractVector{Int32})`: assign a set of values to the `adcCounts` vector member
