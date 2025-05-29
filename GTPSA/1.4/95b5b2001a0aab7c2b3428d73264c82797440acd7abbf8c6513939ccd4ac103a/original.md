```
Descriptor(vos::Vector{<:Integer}, mo::Integer, pos::Vector{<:Integer}, po::Integer)::Descriptor
```

Creates a TPSA `Descriptor` with `length(vos)` variables with individual truncation  orders specified in `vos`, and `length(pos)` parameters with individual truncation  orders specified in `pos`. The maximum truncation order including both variables and  parameters is `mo`, and the truncation order for just the parameters part of the is `po`.

### Input

  * `vos` – `Vector` of the individual truncation orders of each variable
  * `mo`  – Maximum truncation order of the TPSA including variables and parameters
  * `pos` – `Vector` of the individual truncation orders of each parameter
  * `po` – Truncation order of the parameters part of a monomial
