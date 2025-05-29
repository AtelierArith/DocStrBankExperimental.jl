```
latent_heat_vaporization(Tair)
```

Latent heat of vaporization as a function of air temperature using 

$\lambda = (2.501 - 0.00237 \, Tair) 10^6$.

# Arguments:

  * Tair:  Air temperature (deg C)

# Value

$\lambda$: Latent heat of vaporization (J kg-1) 

# References

  * Stull, B*, 1988: An Introduction to Boundary Layer Meteorology (p*641)           Kluwer Academic Publishers, Dordrecht, Netherlands
  * Foken, T, 2008: Micrometeorology_ Springer, Berlin, Germany

```@example
latent_heat_vaporization.(5:5:45)        
```
