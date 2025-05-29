```
Norman_Longwave(ϵ=0.98, ϵ_g=1.0, T_veg=25, T_g=20, L_sky=400)

Longwave radiation transfer through canopy using Norman (1979)
```

# Arguments

  * `ϵ`     : Leaf emissivity
  * `ϵ_g`   : Ground (soil) emissivity
  * `LAI`   : Leaf area index (m2/m2)
  * `L_sky` : Atmospheric longwave radiation (W/m2)

# Examples

```julia
n = 50
ϵ = [1.0; fill(0.98, n - 1)]
T_leaf = [20.0; fill(25.0, n - 1)]
τd = ones(n) .* 0.915     # transmittance of diffuse radiation through each leaf layer
L_up, L_dn, Rln, Rln_soil, Rln_veg = Norman_Longwave(T_leaf, ϵ, τd)

# irup  = 447.16643
# irveg = -75.54891
# irsoi =  28.38247
```
