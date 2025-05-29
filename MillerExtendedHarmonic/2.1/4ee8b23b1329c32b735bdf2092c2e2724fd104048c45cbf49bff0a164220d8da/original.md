```
    MXH!(mxh::MXH, pr::AbstractVector{<:Real}, pz::AbstractVector{<:Real}, R0::Real, Z0::Real, a::Real, b::Real;
θ::AbstractVector{<:Real}, Δθᵣ::AbstractVector{<:Real}, dθ::AbstractVector{<:Real}, Fm::AbstractVector{<:Real},
optimize_fit=false, spline=false)
```

Like MXH() but operates in place. θ, Δθᵣ, dθ, Fm are work arrays vectors that can be preallocated if desired

N.B.: This function potentially reorders pr and pz in-place
