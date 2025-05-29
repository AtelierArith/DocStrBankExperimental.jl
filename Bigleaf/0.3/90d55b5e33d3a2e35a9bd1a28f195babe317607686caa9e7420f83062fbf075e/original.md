```
compute_Ram(::ResistanceWindProfile(), ustar; 
  zr, d, z0m, psi_h, constants=BigleafConstants())
compute_Ram!(df, method::ResistanceWindProfile();  
  zr, d, z0m, psi_h = df.psi_h, kwargs...)

compute_Ram(::ResistanceWindZr(), ustar, wind)
compute_Ram!(df, method::ResistanceWindZr(); kwargs...)
```

Estimate bulk aerodynamic conductance.

# Arguments

  * `ustar`          : Friction velocity (m s-1)
  * `df`             : DataFrame with above columns
  * `zr`             : Instrument (reference) height (m)
  * `d`              : Zero-plane displacement height (-), can be estimated using                      [`roughness_parameters`](@ref)
  * `z0m`            : Roughness length for momentum (m). Can be estimated using                     from [`roughness_parameters`](@ref)
  * `psi_h`          : the value of the stability function for heat and water vapor (-)                    see [`stability_correction`](@ref)

# Details

The aerodynamic resistance for momentum $R_{a_m}$ is given by (`Ram_method = ResistanceWindZr()`):

$R_{a_m} = u/{u^*}^2$

Where u is the horizontal wind velocity.  Note that this formulation accounts for changes in atmospheric stability, and does not  require an additional stability correction function. 

An alternative method to calculate $Ra_m$ is provided (`Ram_method = ResistanceWindProfile()`):

$R_{a_m} = (ln((z_r - d)/z_{0m}) - \psi_h) / (k \, u^*)$

If the roughness parameters `z0m` and `d` are unknown, they can be estimated using [`roughness_parameters`](@ref). The argument `stab_formulation` determines the stability  correction function used to account for the effect of atmospheric stability on `Ra_m`  (`Ra_m` is lower for unstable and higher for stable stratification). Stratification is based  on a stability parameter `zeta` $\zeta=(z-d/L)$, where `z` is the height,  `d` the zero-plane displacement height, and `L` the Monin-Obukhov length, calculated with  [`Monin_Obukhov_length`](@ref) The stability correction function is chosen by the argument `stab_formulation`.  Options are `Dyer1970()` and `Businger1971()` and `NoStabilityCorrection()`.

# Note

For adding aerodynamic conductance for other species see [`add_Ga!`](@ref).

# Value

Aerodynamic resistance for momentum transfer (s m-1) ($Ra_m$)

# References

  * Verma, S., 1989: Aerodynamic resistances to transfers of heat, mass and momentum. In: Estimation of areal evapotranspiration, IAHS Pub, 177, 13-20.
  * Verhoef, A., De Bruin, H., Van Den Hurk, B., 1997: Some practical notes on the parameter kB^(-1) for sparse vegetation. Journal of Applied Meteorology, 36, 560-572.
  * Hicks, B*B., Baldocchi, D*D., Meyers, T*P., Hosker, J*R., Matt, D_R., 1987: A preliminary multiple resistance routine for deriving dry deposition velocities from measured quantities. Water, Air, and Soil Pollution 36, 311-330.
  * Monteith, J*L., Unsworth, M*H., 2008: Principles of environmental physics. Third Edition. Elsevier Academic Press, Burlington, USA.

# See also

[`aerodynamic_conductance!`](@ref), [`add_Ga!`](@ref)
