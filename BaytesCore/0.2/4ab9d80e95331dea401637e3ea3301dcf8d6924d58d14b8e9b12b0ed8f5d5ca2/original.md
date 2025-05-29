```julia
struct Expanding <: BaytesCore.DataStructure
```

Determines if data size for sampler is increasing over time.

# Fields

  * `index::BaytesCore.Iterator`: maximal visible index
