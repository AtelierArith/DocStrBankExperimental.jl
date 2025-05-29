```
AbstractIsotopeScalar <: AbstractData
```

An IsotopeScalar represents a quantity or flux with isotopic composition. Can be added, subtracted, multiplied by a scalar, and decomposed into components with the same (bulk) transport properties.

# Implementation

Each IsotopeScalar should be added to `IsotopeTypes`, and implement:

  * get_total(is::IsotopeScalar) -> total
  * arithmetic operations +/- (ie IsotopeScalars can be added and subtracted) and *number, /number  (IsotopeScalars can be scaled by a real number).
  * methods of the [`AbstractData`](@ref) interface

and optional isotope-specific functions, eg for a single isotope:

  * isotope_totaldelta(::Type{<: IsotopeScalar}, total, delta) -> IsotopeScalar()
  * get_delta(is::IsotopeScalar) -> delta
