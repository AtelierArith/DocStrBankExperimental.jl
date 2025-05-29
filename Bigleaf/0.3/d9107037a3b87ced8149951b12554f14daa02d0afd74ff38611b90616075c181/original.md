```
ms_to_mol(G_ms,Tair,pressure; constants=BigleafConstants())
mol_to_ms(G_mol,Tair,pressure; constants=BigleafConstants())
```

Converts conductances from mass (m s-1) to molar units (mol m-2 s-1), or vice versa

# Details

The conversions are given by

  * $G_{mol} = G_{ms}  \, pressure / (Rgas  Tair)$
  * $G_{ms} = G_{mol}  \, (Rgas  Tair) / pressure$

where Tair is in Kelvin and pressure in Pa (converted from kPa internally).

# References

Jones, H*G* 1992_ Plants and microclimate: a quantitative approach to    environmental plant physiology_   2nd Edition*, Cambridge University Press, Cambridge* 428 

# Examples

```jldoctest; output = false
G_ms,Tair,pressure = 0.005,25.0,100.0
rmol = ms_to_mol(G_ms,Tair,pressure)
≈(rmol, 0.2017, atol =1e-4)
# output
true
```
