```
struct NBodyChargeCloud{T, N, SH} <: AbstractChargeCloud
```

Struct which defines a charge cloud consisting of multiple point-like charge carriers, initially distributed around a given center.

## Parametric Types

  * `T`: Precision type.
  * `N`: Number of shells.
  * `SH`: Geometry of the shells.

## Fields

  * `locations::Vector{CartesianPoint{T}}`: Positions of the charge carriers that are part of the charge cloud.
  * `energies::Vector{T}`: Energies of the respective charge carriers, in the same order as `locations`.
  * `shell_structure::SH`: Initial geometry of the charge carriers around the `center` point, relevant for plotting.
