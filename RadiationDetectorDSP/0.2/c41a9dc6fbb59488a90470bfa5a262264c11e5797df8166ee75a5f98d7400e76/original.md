```
struct CUSPChargeFilter <: AbstractRadFIRFilter
```

CUSP filter.

For the definition the filter and a discussion of the filter properties, see

Constructors:

  * `CUSPChargeFilter(; fields...)`

Fields:

  * `sigma::Union{Real, Unitful.AbstractQuantity{<:Real}}`: equivalent of shaping time (τₛ) Default: 450
  * `toplen::Union{Real, Unitful.AbstractQuantity{<:Real}}`: length of flat top (FT) Default: 10
  * `tau::Union{Real, Unitful.AbstractQuantity{<:Real}}`: decay constant of the exponential Default: 20
  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`: total length of the filter (L) Default: 100
  * `beta::AbstractFloat`: scaling factor Default: 100.0
