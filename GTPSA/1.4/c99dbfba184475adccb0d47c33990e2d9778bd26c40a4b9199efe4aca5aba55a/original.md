```
compose!(m, m2, m1) -> m
```

Composes the `TPS`s (or `TPS` maps) `m2 ∘ m1`, and sets `m` equal to the result. If  the GTPSA has more than 1 variable or parameter, then `m1` must be an array with length  equal to the total number of variables and parameters.

# Arguments

  * `m::Union{AbstractArray{TPS{T,D}},TPS{T,D}}`
  * `m2::Union{AbstractArray{TPS{T,D2}},TPS{T,D2}}`
  * `m1::Union{AbstractArray{TPS{T,D1}},TPS{T,D1}}`
