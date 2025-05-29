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

MXH()と似ていますが、インプレースで動作します。θ、Δθᵣ、dθ、Fmは、必要に応じて事前に割り当て可能な作業配列ベクトルです。
