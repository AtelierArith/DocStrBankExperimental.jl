```
translate!(m, m1, x) -> m
```

Sets `m` to `m1` with its expansion point translated by `x`.

# Arguments

  * `m::Union{AbstractArray{TPS{T,D}},TPS{T,D}}`    – Output `TPS` or `TPS` map containing `m` translated by `x`
  * `m1::Union{AbstractArray{TPS{T,D1}},TPS{T,D1}}` – `TPS` or `TPS` map to translate by `x`
  * `x::Union{Ref{T},AbstractArray{T}}`             – Amount to translate the expansion point of `m1` by each variable. If the GTPSA has only 1 variable, then this may be a `Ref`.
