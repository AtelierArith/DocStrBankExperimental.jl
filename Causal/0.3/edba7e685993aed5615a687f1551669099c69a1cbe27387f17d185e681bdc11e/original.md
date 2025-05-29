```julia
mutable struct Inpin{T} <: Causal.AbstractPin{T}
```

Constructs and `InPut` pin. The data flow from `Inpin` is inwards to the pin i.e., data is read from links of `InPort`.

# Fields

  * `link::Union{Missing, Causal.Link{T}} where T`: Links bound to the inpin. The data read from input is read from the links
  * `id::Base.UUID`: Unique identifier
