```julia
τ_B(cfun, lim, τsb; rtol, atol)

```

Calculate the bath time scale $τ_B$ from the correlation function `cfun`. $τ_B$ is defined as $τ_B/τ_{SB} = ∫_0^T τ|C(τ)|dτ$. The upper limit of the integration $T$ is specified by `lim`. `τsb` is the other bath time scale $1/τ_{SB}=∫_0^∞ |C(τ)|dτ$. `atol` and `rtol` are the absolute and relative error tolerance for the integration.
