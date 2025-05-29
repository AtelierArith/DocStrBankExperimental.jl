```
stability_correction(zeta; 
  stab_formulation=Dyer1970())
stability_correction(z,d, Tair,pressure,ustar,H; constants,
  stab_formulation=Dyer1970())
stability_correction!(df; zeta, z, d; 
  stab_formulation=Dyer1970(), constants =BigleafConstants())
```

Integrated Stability Correction Functions for Heat and Momentum

# Arguments

  * `zeta`             : Stability parameter zeta (-)
  * `Tair`,`pressure`,`ustar`,`H` : see [`Monin_Obukhov_length`](@ref)
  * `z`,`d`            : see [`stability_parameter`](@ref)
  * `df`  : DataFrame containing the variables required by [`Monin_Obukhov_length`](@ref)
  * `stab_formulation` : Formulation for the stability function. Either            `Dyer1970()`, or `Businger1971()` or `NoStabilityCorrection()`

In the second and third form computes `zeta` by [`stability_parameter`](@ref) and [`Monin_Obukhov_length`](@ref) and requires respective arguments.

# Details

These dimensionless values are needed to correct deviations from the exponential wind profile under non-neutral conditions. The functions give the integrated form of the universal functions. They depend on the value of the stability parameter $\zeta$, a function of height `z`, which can be calculated from the function [`stability_parameter`](@ref). The integration of the universal functions is:

$\psi = -x * \zeta$ 

for stable atmospheric conditions ($\zeta$ >= 0), and

$\psi = 2 * log( (1 + y(\zeta)) / 2)$

for unstable atmospheric conditions ($\zeta$ < 0).

The different formulations differ in their value of x and y.

# Value

a NamedTuple with the following columns:

  * `psi_h`: the value of the stability function for heat and water vapor (-)
  * `psi_m`: the value of the stability function for momentum (-)

# References

  * Dyer, A_J., 1974: A review of flux-profile relationships.  Boundary-Layer Meteorology 7, 363-372.
  * Dyer, A. J., Hicks, B_B., 1970: Flux-Gradient relationships in the constant flux layer. Quart. J. R. Meteorol. Soc. 96, 715-721.
  * Businger, J_A., Wyngaard, J. C., Izumi, I., Bradley, E. F., 1971: Flux-Profile relationships in the atmospheric surface layer.  J. Atmospheric Sci. 28, 181-189.
  * Paulson, C_A., 1970: The mathematical representation of wind speed and temperature profiles in the unstable atmospheric surface layer. Journal of Applied Meteorology 9, 857-861. Foken, T, 2008: Micrometeorology. Springer, Berlin, Germany.

# Examples

```jldoctest; output = false
using DataFrames
zeta = -2:0.5:0.5
df2 = DataFrame(stability_correction.(zeta; stab_formulation=Businger1971()))                         
propertynames(df2) == [:psi_h, :psi_m]
# output
true
```
