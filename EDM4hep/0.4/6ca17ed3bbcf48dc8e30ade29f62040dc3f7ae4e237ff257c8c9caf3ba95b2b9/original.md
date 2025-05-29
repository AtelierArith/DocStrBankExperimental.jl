Tracker hit

  * Author: F.Gaede, DESY

# Fields

  * `cellID::UInt64`: ID of the sensor that created this hit
  * `type::Int32`: type of raw data hit, either one of edm4hep::RawTimeSeries, edm4hep::SIMTRACKERHIT - see collection parameters "TrackerHitTypeNames" and "TrackerHitTypeValues".
  * `quality::Int32`: quality bit flag of the hit.
  * `time::Float32`: time of the hit [ns].
  * `eDep::Float32`: energy deposited on the hit [GeV].
  * `eDepError::Float32`: error measured on EDep [GeV].
  * `position::Vector3d`: hit position in [mm].
  * `covMatrix::SVector{6,Float32}`: covariance of the position (x,y,z), stored as lower triangle matrix. i.e. cov(x,x) , cov(y,x) , cov(y,y) , cov(z,x) , cov(z,y) , cov(z,z)
  * `rawHits::PVector{ObjectID}`: raw data hits. Check getType to get actual data type.

# Methods

  * `setRawHits(object::TrackerHit, v::AbstractVector{ObjectID})`: assign a set of values to the `rawHits` vector member
