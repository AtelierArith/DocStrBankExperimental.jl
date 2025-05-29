```
equilibrium_imposed_ET(Tair,pressure,VPD,Gs, Rn; ...)
equilibrium_imposed_ET!(df; ...)
```

Evapotranspiration (ET) split up into imposed ET and equilibrium ET.

# Arguments

  * `Tair`      : Air temperature (deg C)
  * `pressure`  : Atmospheric pressure (kPa)
  * `VPD`       : Air vapor pressure deficit (kPa)
  * `Gs`        : surface conductance to water vapor (m s-1)
  * `Rn`        : Net radiation (W m-2)

optional : 

  * `G=0`       : Ground heat flux (W m-2)
  * `S=0`       : Sum of all storage fluxes (W m-2)
  * `Esat_formula=Sonntag1990()`: formula used in [`Esat_from_Tair`](@ref)
  * `constants=`[`BigleafConstants`](@ref)`()`: physical constants (cp, eps)

# Details

Total evapotranspiration can be written in the form (Jarvis & McNaughton 6):

$ET = \Omega \mathit{ET}_{eq} + (1 - \Omega) \mathit{ET}_{imp}$

where $\Omega$ is the decoupling coefficient as calculated from [`decoupling`](@ref). `ET_eq` is the equilibrium evapotranspiration i.e., the ET rate that would occur under uncoupled conditions, where the budget is dominated by radiation (when Ga -> 0):

$ET_{eq} = (\Delta \, (R_n - G - S) \, \lambda) / ( \Delta \gamma)$

where $\Delta$ is the slope of the saturation vapor pressur(kPa K-1), $\lambda$ is the latent heat of vaporization (J kg-1), and $\gamma$ is the psychrometric constant (kPa K-1). `ET_imp` is the imposed evapotranspiration rate, the ET rate that would occur under fully coupled conditions (when Ga -> inf):

$ET_{imp} = (\rho \, c_p \, \mathit{VPD} ~ G_s \, \lambda) / \gamma$

where $\rho$ is the air density (kg m-3).

# Value

A `NamedTuple` or `DataFrame` with the following columns:

  * `ET_eq`: Equilibrium ET (kg m-2 s-1)
  * `ET_imp`: Imposed ET (kg m-2 s-1)
  * `LE_eq`: Equilibrium LE (W m-2)
  * `LE_imp`: Imposed LE (W m-2)

# References

  * Jarvis, P*G., McNaughton, K*G., 1986: Stomatal control of transpiration: scaling up from leaf to region. Advances in Ecological Rese1-49.
  * Monteith, J*L., Unsworth, M*H., 2008: Principles of ironmPhysics. 3rd edition. Academic Press, London.

# Examples

```jldoctest; output = false
Tair,pressure,Rn, VPD, Gs = 20.0,100.0,50.0, 0.5, 0.01
ET_eq, ET_imp, LE_eq, LE_imp = equilibrium_imposed_ET(Tair,pressure,VPD,Gs, Rn)    
≈(ET_eq, 1.399424e-05; rtol = 1e-5)
# output
true
```
