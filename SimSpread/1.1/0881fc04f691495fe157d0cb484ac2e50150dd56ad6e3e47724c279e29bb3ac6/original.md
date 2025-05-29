```
cutoff(x::T, α::T, weighted::Bool=false) where {T<:AbstractFloat}
```

Transform `x` based in SimSpread's similarity cutoff function.

# Arguments

  * `x::AbstractFloat` : Value to transform
  * `α::AbstractFloat` : Similarity cutoff
  * `weighted::Bool` : Apply weighting function to outcome (default = false)
