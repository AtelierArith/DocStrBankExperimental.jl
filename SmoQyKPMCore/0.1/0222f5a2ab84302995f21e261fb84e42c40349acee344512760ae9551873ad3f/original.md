```
kpm_density!(
    ρ::AbstractVector{T},
    ϵ::AbstractVector{T},
    μ::AbstractVector{T},
    bounds,
    r2rplan = FFTW.plan_r2r!(ρ, FFTW.REDFT01)
) where {T<:AbstractFloat}
```

Given the KPM moments $\mu$, calculate the spectral density $\rho(\epsilon)$ and corresponding energies $\epsilon$ where it is evaluated. Here `bounds` is bounds the eigenspecturm, such that the bandwidth is given by `W = bounds[2] - bounds[1]`.
