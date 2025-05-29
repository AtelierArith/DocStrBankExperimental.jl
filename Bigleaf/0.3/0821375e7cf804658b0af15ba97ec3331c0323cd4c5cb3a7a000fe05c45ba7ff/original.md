```
psychrometric_constant(Tair,pressure; ...)
```

Computes the psychrometric 'constant'.

# Arguments

  * Tair:      Air temperature (deg C)
  * pressure:  Atmospheric pressure (kPa)

optional 

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries    cp, eps

# Details

The psychrometric constant ($\gamma$) is given as:

$\gamma = cp * pressure / (eps * \lambda)$

where $\lambda$ is the latent heat of vaporization (J kg-1),   as calculated from [`latent_heat_vaporization`](@ref).

# Value

the psychrometric constant (kPa K-1)

# References

Monteith J.L., Unsworth M.H., 2008: Principles of Environmental Physics.             3rd Edition. Academic Press, London.

# Examples

```@example doc
psychrometric_constant.(5.0:5.0:25.0, 100)
```
