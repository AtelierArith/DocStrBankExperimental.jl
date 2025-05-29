```
umolCO2_to_gC(CO2_flux; constants=BigleafConstants())
gC_to_umolCO2(C_flux; constants=BigleafConstants())
```

Convert CO2 quantities from (umol CO2 m-2 s-1) to (g C m-2 d-1) and vice versa.

# Arguments

  * CO2_flux  CO2 flux (umol CO2 m-2 s-1)
  * C_flux    Carbon (C) flux (gC m-2 d-1)
  * `constants`: dictionary from [`BigleafConstants`](@ref) with entries: Cmol, umol2mol, mol2umol, kg2g, g2kg, says2seconds

# Examples

```@example
umolCO2_to_gC(20)  # gC m-2 d-1
```
