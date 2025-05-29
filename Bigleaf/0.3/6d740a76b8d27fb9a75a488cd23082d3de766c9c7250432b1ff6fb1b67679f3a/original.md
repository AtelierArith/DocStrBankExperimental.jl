```
stability_parameter(z,d,MOL)
stability_parameter(z,d,Tair, pressure, ustar, H; constants)
stability_parameter!(df::AbstractDataFrame; z,d, MOL=nothing, constants)
```

calculates stability parameter "zeta", a parameter characterizing stratification in the  lower atmosphere.

# Arguments

  * `z`   : height (m)
  * `d`   : Zero-plane displacement height (m)
  * `MOL` : Monin-Obukhov-length L (m)
  * `df`  : DataFrame containing the variables required by [`Monin_Obukhov_length`](@ref)

optional

  * `constants=`[`BigleafConstants`](@ref)`()`

In the second variant and if `MOL=nothing` in the DataFrame variants, MOL is computed by  [`Monin_Obukhov_length`](@ref).

# Details

The stability parameter $\zeta$ is given by:

$\zeta = (z - d) / L$

where L is the Monin-Obukhov length (m), calculated by [`Monin_Obukhov_length`](@ref). The displacement height can  be estimated from the function [`roughness_parameters`](@ref).

# Value

$\zeta$: stability parameter (-). The nonmutainting DataFrame variant returns a vector. The mutating variant modifies or adds column [`:zeta`].

```jldoctest; output = false
using DataFrames
df = DataFrame(Tair=25.0, pressure=100.0, ustar=0.2:0.1:1.0, H=40:20.0:200)
z=40;d=15
zeta = stability_parameter.(z,d, df.Tair, df.pressure, df.ustar, df.H)
all(zeta .< 0)
# output
true
```
