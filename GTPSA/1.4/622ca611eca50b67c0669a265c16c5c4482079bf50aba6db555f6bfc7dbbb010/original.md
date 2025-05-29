```
Descriptor(vos::Vector{<:Integer}, mo::Integer)::Descriptor
```

Creates a TPSA `Descriptor` with `length(vos)` variables with individual truncation  orders specified in the Vector `vos`, and a maximum truncation order `mo` for the TPSA.

### Input

  * `vos` – `Vector` of the individual truncation orders of each variable
  * `mo`  – Maximum truncation order of the TPSA, <= sum(vos)
