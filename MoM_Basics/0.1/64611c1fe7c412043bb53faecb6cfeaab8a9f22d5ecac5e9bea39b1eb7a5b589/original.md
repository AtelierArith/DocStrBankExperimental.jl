```
radiationIntensityU_m(md::MagneticDipole{FT}, θϕ::θϕInfo{FT}) where {FT<:Real}
```

计算磁流源的辐射强度函数 $U_m(θ, ϕ) = \frac{Y_0}{8λ_0²}(|L_θ|² + |L_ϕ|²)$。
