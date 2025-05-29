```julia
struct Rolling <: BaytesCore.DataStructure
```

Determines if data size for sampler is rolled forward over time.

# Fields

  * `length::Int64`: Rolling window.
  * `index::BaytesCore.Iterator`: maximal visible index
