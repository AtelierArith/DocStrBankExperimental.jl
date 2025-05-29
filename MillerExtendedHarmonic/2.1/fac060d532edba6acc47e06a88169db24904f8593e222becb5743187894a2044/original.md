```
    MXH!(
    mxh::MXH,
    pr::AbstractVector{<:Real},
    pz::AbstractVector{<:Real};
    θ=similar(pr),
    Δθᵣ=similar(pr),
    dθ=similar(pr),
    Fm=similar(pr),
    optimize_fit=false,
    spline=false,
    rmin=0.0,
    rmax=0.0,
    zmin=0.0,
    zmax=0.0)
```

Like MXH() but operates in place. θ, Δθᵣ, dθ, Fm are work arrays vectors that can be preallocated if desired
