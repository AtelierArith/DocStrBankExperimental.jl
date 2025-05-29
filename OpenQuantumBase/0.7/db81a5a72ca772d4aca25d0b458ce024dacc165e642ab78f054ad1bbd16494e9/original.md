```julia
τ_SB(cfun; lim, rtol, atol)

```

Calculate the bath time scale $τ_{SB}$ from the bath correlation function `cfun`. $τ_{SB}$ is defined as $1/τ_{SB}=∫_0^∞ |C(τ)|dτ$. The upper limit of the integration can be modified using keyword `lim`. `atol` and `rtol` are the absolute and relative error tolerance of the integration.
