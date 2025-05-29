TrackState

# Fields

  * `location::Int32`: for use with At{Other|IP|FirstHit|LastHit|Calorimeter|Vertex}|LastLocation
  * `D0::Float32`: transverse impact parameter
  * `phi::Float32`: azimuthal angle
  * `omega::Float32`: is the signed curvature of the track in [1/mm].
  * `Z0::Float32`: longitudinal impact parameter
  * `tanLambda::Float32`: lambda is the dip angle of the track in r-z
  * `time::Float32`: time of the track at this trackstate
  * `referencePoint::Vector3f`: Reference point of the track parameters, e.g. the origin at the IP, or the position  of the first/last hits or the entry point into the calorimeter. [mm]
  * `covMatrix::SVector{21,Float32}`: lower triangular covariance matrix of the track parameters.  the order of parameters is  d0, phi, omega, z0, tan(lambda), time. the array is a row-major flattening of the matrix.
