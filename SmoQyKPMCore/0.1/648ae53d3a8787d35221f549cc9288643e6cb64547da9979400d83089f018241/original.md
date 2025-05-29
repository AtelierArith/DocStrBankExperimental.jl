```
kpm_density(
    N::Int, μ::T, W
) where {T<:AbstractVector}
```

Given the KPM moments $\mu$, evaluate the corresponding spectral density $\rho(\epsilon)$ at $N$ energy points $\epsilon$, where $W$ is the spectral bandwidth or the bounds of the spectrum. This function returns both $\rho(\epsilon)$ and $\epsilon$.
