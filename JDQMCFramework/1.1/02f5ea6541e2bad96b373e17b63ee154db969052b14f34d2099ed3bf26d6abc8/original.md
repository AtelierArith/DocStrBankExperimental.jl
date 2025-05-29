```
eval_length_imaginary_axis(
    β::T,
    Δτ::T
)::Int where {T<:AbstractFloat}
```

Given an inverse temperature `β` and discretization in imaginary time `Δτ`, return the length of the imaginary time axis `Lτ`.
