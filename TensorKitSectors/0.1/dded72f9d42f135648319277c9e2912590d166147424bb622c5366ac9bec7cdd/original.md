```
struct SectorValues{I<:Sector}
```

Singleton type to represent an iterator over the possible values of type `I`, whose instance is obtained as `values(I)`. For a new `I::Sector`, the following should be defined

  * `Base.iterate(::SectorValues{I}[, state])`: iterate over the values
  * `Base.IteratorSize(::Type{SectorValues{I}})`: `HasLength()`, `SizeUnknown()`   or `IsInfinite()` depending on whether the number of values of type `I` is finite   (and sufficiently small) or infinite; for a large number of values, `SizeUnknown()` is   recommended because this will trigger the use of `GenericGradedSpace`.

If `IteratorSize(I) == HasLength()`, also the following must be implemented:

  * `Base.length(::SectorValues{I})`: the number of different values
  * `Base.getindex(::SectorValues{I}, i::Int)`: a mapping between an index `i` and an   instance of `I`. A fallback implementation exists that returns the `i`th value   of the `SectorValues` iterator.
  * `findindex(::SectorValues{I}, c::I)`: reverse mapping between a value `c::I` and an   index `i::Integer ∈ 1:length(values(I))`. A fallback implementation exists that   linearly searches through the `SectorValues` iterator.
