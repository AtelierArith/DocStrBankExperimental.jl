```
potential_ET(::PriestleyTaylor, Tair, pressure, Rn; G=0.0, S=0.0, ...)
potential_ET(::PriestleyTaylor, Tair, pressure, Rn, G, S; ...)

potential_ET(::PenmanMonteith, Tair, pressure, Rn, VPD, Ga_h;
  G=zero(Tair),S=zero(Tair), ...)
fpotential_ET(::PenmanMonteith, Tair, pressure, Rn, VPD, Ga_h, G, S; ...)

potential_ET!(df, approach; ...)
```

Potential evapotranspiration according to Priestley & Taylor 1972 or the Penman-Monteith equation with a prescribed surface conductance.

# Arguments

  * `Tair`:      Air temperature (degC)
  * `pressure`:  Atmospheric pressure (kPa)
  * `Rn`:        Net radiation (W m-2)
  * `VPD`:       Vapor pressure deficit (kPa)
  * `Ga`:        Aerodynamic conductance to heat/water vapor (m s-1)
  * `df`:        DataFrame with the above variables
  * `approach`:  Approach used: Either `PriestleyTaylor()`  or `PenmanMonteith()`.

optional:

  * `G=0.0`:         Ground heat flux (W m-2). Defaults to zero.
  * `S=0.0`:         Sum of all storage fluxes (W m-2) . Defaults to zero.
  * `constants=`[`BigleafConstants`](@ref)`()`: physical constants (cp, eps, Rd, Rgas)

for `PriestleyTaylor`:

  * `alpha = 1.26`:   Priestley-Taylor coefficient

for PenmanMonteith:

  * `Gs_pot = 0.6`:    Potential/maximum surface conductance (mol m-2 s-1);
  * `Esat_formula`: formula used in [`Esat_from_Tair`](@ref)

# Details

Potential evapotranspiration is calculated according to Priestley & Taylor, 1972 (`approach = PriestleyTaylor()`:

$\mathit{LE}_{pot} = (\alpha \, \Delta \, (Rn - G - S)) / (\Delta + \gamma)$

$\alpha$ is the Priestley-Taylor coefficient, $\Delta$ is the slope  of the saturation vapor pressure curve (kPa K-1), and $\gamma$ is the  psychrometric constant (kPa K-1).

If `approach = PenmanMonteith()`, potential evapotranspiration is calculated according to the Penman-Monteith equation:

$\mathit{LE}_{pot} = (\Delta \, (R_n - G - S) + \rho \, c_p \, \mathit{VPD} \; G_a) /  (\Delta + \gamma \, (1 + G_a/G_{s pot})$

where $\Delta$ is the slope of the saturation vapor pressure curve (kPa K-1), $\rho$ is the air density (kg m-3),  and $\gamma$ is the psychrometric constant (kPa K-1). The value of $G_{s pot}$ is typically a maximum value of $G_s$ observed at the site,  e.g. the $90^{th}$ percentile of $G_s$ within the growing season.

Ground heat flux and storage heat flux `G` or `S` are provided as optional  arguments. In the input-explicit variants, they default to zero. In the data-frame arguments, they default to missing, which results in assuming them to be zero which is displayed in a log-message. Note that in difference to the bigleaf R package, you explicitly need to care for missing values (see examples).

# Value

NamedTuple with the following entries:

  * `ET_pot`: Potential evapotranspiration (kg m-2 s-1)
  * `LE_pot`: Potential latent heat flux (W m-2)

# References

  * Priestley, C*H*B., Taylor, R_J., 1972: On the assessment of surface heat flux and evaporation using large-scale parameters. Monthly Weather Review 100, 81-92.
  * Allen, R*G., Pereira L*S., Raes D., Smith M., 1998: Crop evapotranspiration - Guidelines for computing crop water requirements - FAO Irrigation and drainage paper 56.
  * Novick, K_A., et al. 2016: The increasing importance of atmospheric demand for ecosystem water and carbon fluxes. Nature Climate Change 6, 1023 - 1027.

# See also

[`surface_conductance`](@ref)

# Examples

Calculate potential ET of a surface that receives a net radiation of 500 Wm-2 using Priestley-Taylor:

```jldoctest; output=false
Tair, pressure, Rn = 30.0,100.0,500.0
ET_pot, LE_pot = potential_ET(PriestleyTaylor(), Tair, pressure, Rn)    
≈(ET_pot, 0.000204; rtol = 1e-2)
# output
true
```

Calculate potential ET for a surface with known Gs (0.5 mol m-2 s-1) and Ga (0.1 m s-1) using Penman-Monteith:

```jldoctest; output=false
Tair, pressure, Rn = 30.0,100.0,500.0
VPD, Ga_h, Gs_pot = 2.0, 0.1, 0.5
ET_pot, LE_pot = potential_ET(
  PenmanMonteith(), Tair,pressure,Rn,VPD, Ga_h; Gs_pot)    
# now cross-check with the inverted equation
Gs_ms, Gs_mol = surface_conductance(
  InversePenmanMonteith(), Tair,pressure,VPD,LE_pot,Rn,Ga_h)
Gs_mol ≈ Gs_pot
# output
true
```

DataFrame variant with explicitly replacing missings using `coalesce.`:

```jldoctest; output=false
using DataFrames
df = DataFrame(
  Tair = 20.0:1.0:30.0,pressure = 100.0, Rn = 500.0, G = 105.0, VPD = 2.0, 
  Ga_h = 0.1) 
allowmissing!(df, Cols(:G)); df.G[1] = missing
#
# need to provide G explicitly
df_ET = potential_ET!(copy(df), PriestleyTaylor(); G = df.G)    
ismissing(df_ET.ET_pot[1])
#
# use coalesce to replace missing values by zero
df_ET = potential_ET!(
  copy(df), PriestleyTaylor(); G = coalesce.(df.G, zero(df.G)))    
!ismissing(df_ET.ET_pot[1])
# output
true
```
