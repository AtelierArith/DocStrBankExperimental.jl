```julia
mutable struct Outpin{T} <: Causal.AbstractPin{T}
```

Constructs and `OutPut` pin. The data flow from `Outpin` is outwards from the pin i.e., data is written from `OutPort` to its links.

# Fields

  * `links::Union{Missing, Array{Causal.Link{T}, 1}} where T`: Links bound to the outpin. The data written to pin is transfered to all the links
  * `id::Base.UUID`: Unique identifier
