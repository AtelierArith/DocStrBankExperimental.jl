```
struct ZACChargeFilter <: AbstractRadFIRFilter
```

Zero area cusp (ZAC) filter.

For the definition the filter and a discussion of the filter properties, see ["Improvement of the energy resolution via an optimized digital signal processing in GERDA Phase I", Eur. Phys. J. C 75, 255 (2015)](https://doi.org/10.1140/epjc/s10052-015-3409-6).

Constructors:

  * `ZACChargeFilter(; fields...)`

Fields:

  * `sigma::Union{Real, Unitful.AbstractQuantity{<:Real}}`: equivalent of shaping time (τₛ) Default: 450
  * `toplen::Union{Real, Unitful.AbstractQuantity{<:Real}}`: length of flat top (FT) Default: 10
  * `tau::Union{Real, Unitful.AbstractQuantity{<:Real}}`: decay constant of the exponential Default: 20
  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`: total length of the filter (L) Default: 100
  * `beta::AbstractFloat`: scaling factor Default: 100.0
