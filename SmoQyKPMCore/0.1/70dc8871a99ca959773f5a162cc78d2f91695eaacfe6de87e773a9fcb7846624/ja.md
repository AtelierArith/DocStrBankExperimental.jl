```
kpm_density!(
    ρ::AbstractVector{T},
    ϵ::AbstractVector{T},
    μ::AbstractVector{T},
    W::T,
    r2rplan = FFTW.plan_r2r!(ρ, FFTW.REDFT01),
) where {T<:AbstractFloat}
```

KPMモーメント$\mu$を与えられた場合、スペクトル密度$\rho(\epsilon)$と評価される対応するエネルギー$\epsilon$を計算します。ここで$W$はスペクトル帯域幅です。
