```
kpm_density!(
    ρ::AbstractVector{T},
    ϵ::AbstractVector{T},
    μ::AbstractVector{T},
    bounds,
    r2rplan = FFTW.plan_r2r!(ρ, FFTW.REDFT01)
) where {T<:AbstractFloat}
```

KPMモーメント$\mu$を与えられた場合、スペクトル密度$\rho(\epsilon)$と評価される対応するエネルギー$\epsilon$を計算します。ここで`bounds`は固有スペクトルの境界を示し、帯域幅は`W = bounds[2] - bounds[1]`で与えられます。
