```julia
Diffusivity(
    D0::T = 59.98               # [cm^2/sec] Maximum diffusion coefficient
    D0_logsigma::T = log(2)/2   # [unitless] log uncertainty (default = log(2)/2 = a factor of 2 two-sigma)
    Ea::T = 205.94              # [kJ/mol] Activation energy
    Ea_logsigma::T = log(2)/2   # [unitless] log uncertainty (default = log(2)/2 = a factor of 2 two-sigma)
)
```

A generic diffusivity model, with user-specified D0 and Ea. Default values are appropriate for argon in k-feldspar.
