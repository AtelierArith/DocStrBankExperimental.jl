```julia
MDDiffusivity(
    D0::NTuple{N,T}             # [cm^2/sec] Maximum diffusivity
    D0_logsigma::NTuple{N,T}    # [unitless] log uncertainty (default = 1/2 = a factor of ℯ two-sigma)
    Ea::T                       # [kJ/mol] Activation energy
    Ea_logsigma::T              # [unitless] log uncertainty (default = 1/2 = a factor of ℯ two-sigma)
)
```

Multiple diffusivities for multiple domains
