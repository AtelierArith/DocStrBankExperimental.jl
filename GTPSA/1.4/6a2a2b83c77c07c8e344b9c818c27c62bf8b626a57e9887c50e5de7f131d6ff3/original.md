```
evaluate!(y, m, x) -> y
```

Evaluates the `TPS` function `m` at the point `x` and mutates `y` to contain the result.

# Arguments

  * `y::Union{Ref{T},AbstractArray{T}}`          – Container to store result of evaluating `m` at `x`
  * `m::Union{TPS{T,D},AbstractArray{TPS{T,D}}}` – `TPS` or `TPS` map to evaluate
  * `x::Union{Ref{T},AbstractArray{T}}`          – Value(s) of the variables to evaluate `m` at
