```
ℱχp(mc::NeXLMatrixCorrection, χ::AbstractFloat, τ::AbstractFloat)
ℱχp(mc::NeXLMatrixCorrection, xray::CharXRay, θtoa::AbstractFloat, τ::AbstractFloat)
ℱχp(mc::MatrixCorrection, xray::CharXRay, θtoa::AbstractFloat, t0::AbstractFloat, t1::AbstractFloat)
```

吸収補正されたϕ(ρz)曲線の部分積分は、ρz = 0からτまで、またはt0からt1までです。
