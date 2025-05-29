```
Station
```

A struct that contains data for a single partition of a Ticra-compatible optimization station file.

### Fields

  * `npoint::Int`: The number of stations in the partition.
  * `u::Vector{Float64}`: A vector of length `npoint` containing the $u$ values (unitless direction cosine along $x$)  of each of the optimization stations in the partition.
  * `v::Vector{Float64}`: A vector of length `npoint` containing the $v$ values (unitless direction cosine along $y$)  of each of the optimization stations in the partition.
  * `goal::Vector{Float64}`: A vector of length `npoint` containing the goal values in dB  for each of the optimization stations in the partition.
  * `weight::Vector{Float64}`: A vector of length `npoint` containing the optimization weights for each of the optimization stations in the partition.
  * `ipol::Vector{Int}`: A vector of length `npoint` containing the polarization codes  for each of the stations in the partition. The codes have the following meanings:

      * 1:  Linear Ludwig 3 x ("copol") component.
      * 2:  Linear Ludwig 3 y ("cxpol") component.
      * 3:  RHCP component.
      * 4:  LHCP component.
      * 5:  Major axis of polarization ellipse.
      * 6:  Minor axis of polarization ellipse.
      * 7:  The ratio co/cx in dB.
      * 8:  The ratio cx/co in dB.
      * 9:  The ratio RHCP/LHCP in dB.
      * 10:  The ratio LHCP/RHCP in dB.
      * 11:  The ratio major/minor in dB.
      * 12:  The ratio minor/major in dB.
      * 13:  The total power 10*log₁₀(‖E⃗‖²) in dB.
  * `rot::Vector{Float64}`: A vector of length `npoint` containing the rotation in degrees of linear polarization reference for each of the optimization stations.
  * `att::Vector{Float64}`: A vector of length `npoint` containing the attenuation in dB ≥ 0  relative to the sub-satellite point.
  * `ID::Vector{String}`: A vector of length `npoint` containing the ID string for each of the optimization stations in the partition. May be empty.
