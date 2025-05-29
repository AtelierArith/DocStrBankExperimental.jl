```
    MXH!(mxh::MXH, pr::AbstractVector{<:Real}, pz::AbstractVector{<:Real}, R0::Real, Z0::Real, a::Real, b::Real;
θ::AbstractVector{<:Real}, Δθᵣ::AbstractVector{<:Real}, dθ::AbstractVector{<:Real}, Fm::AbstractVector{<:Real},
optimize_fit=false, spline=false)
```

MXH()と似ていますが、インプレースで動作します。θ、Δθᵣ、dθ、Fmは、必要に応じて事前に割り当てることができる作業配列ベクトルです。

注：この関数は、prとpzをインプレースで再配置する可能性があります。
