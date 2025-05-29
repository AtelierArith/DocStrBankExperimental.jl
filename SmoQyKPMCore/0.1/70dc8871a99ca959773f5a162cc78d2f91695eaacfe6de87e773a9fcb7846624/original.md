```
kpm_density!(
    ρ::AbstractVector{T},
    ϵ::AbstractVector{T},
    μ::AbstractVector{T},
    W::T,
    r2rplan = FFTW.plan_r2r!(ρ, FFTW.REDFT01),
) where {T<:AbstractFloat}
```

Given the KPM moments $\mu$, calculate the spectral density $\rho(\epsilon)$ and corresponding energies $\epsilon$ where it is evaluated. Here $W$ is the spectral bandwidth.
