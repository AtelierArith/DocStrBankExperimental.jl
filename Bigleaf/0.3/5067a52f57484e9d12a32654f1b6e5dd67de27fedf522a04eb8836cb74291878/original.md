```
roughness_parameters(::RoughnessCanopyHeight()    , zh; frac_d=0.7, frac_z0m=0.1)
roughness_parameters(::RoughnessCanopyHeightLAI(), zh, LAI; cd=0.2, hs=0.01)
roughness_parameters(::Roughness_wind_profile()     , ustar, wind, psi_m; 
  zh, zr, d = 0.7*zh, constants)

roughness_parameters(::Roughness_wind_profile(), ustar, wind, Tair, pressure, H; 
  zh, zr, d = 0.7*zh, stab_formulation=Dyer1970(), constants)
roughness_parameters(::Roughness_wind_profile(), df::DFTable; ...)
```

A approximations of the two roughness parameters displacement height (d) and roughness length for momentum (z0m).

# Arguments

  * `zh`        : Vegetation height (m)
  * `constants=`[`BigleafConstants`](@ref)`()`:

By canopy height:

  * `frac_d`    : Fraction of displacement height on canopy height (-)
  * `frac_z0m`  : Fraction of roughness length on canopy height (-)

By canopy height and LAI

  * `LAI`       : Leaf area index (-)
  * `cd`        : Mean drag coefficient for individual leaves. Defaults to 0.2.
  * `hs`        : roughness length of the soil surface (m).

By wind profile

  * `wind`      : Wind speed at height zr (m s-1)
  * `ustar`     : Friction velocity (m s-1)
  * `zr`        : Instrument (reference) height (m)
  * `d`         : Zero-plane displacement height (-)
  * `psi_m`     : value of the stability function for heat, see [`stability_correction`](@ref)

Another variant estimates of `psi_m` by [`stability_correction`](@ref), which requires further input arguments. For convenience, these arguments can be provided using a DataFrame, however, the result then is not type stable.

# Details

The two main roughness parameters, the displacement height (d) and the roughness length for momentum (z0m) can be estimated from simple empirical relationships with canopy height (zh). If `method = RoughnessCanopyHeight()`, the following formulas are used:  

$d = frac_d * zh$

$z0m = frac_{z0m} * zh$

where $frac_d$ defaults to 0.7 and $frac_{z0m}$ to 0.1.

Alternatively, d and z0m can be estimated from both canopy height and LAI (If `method = RoughnessCanopyHeightLAI()`). Based on data from Shaw & Pereira 1982, Choudhury & Monteith 1988 proposed  the following semi-empirical relations:

$X = cd * LAI$

$d = 1.1 * zh * ln(1 + X^{1/4})$ 

$z0m = hs + 0.3 * zh * X^{1/2}$   for $0 <= X <= 0.2$

$z0m = hs * zh * (1 - d/zh)$   for $0.2 < X$ 

If `method = Roughness_wind_profile()`, z0m is estimated by solving the wind speed profile for z0m:

$z0m = median((zr - d) * exp(-k*wind / ustar - psi_m)$

By default, d in this equation is fixed to 0.7*zh, but can be set to any other value.   

# Value

a NamedTuple with the following components:

  * `d`: Zero-plane displacement height (m)
  * `z0m`: Roughness length for momentum (m)
  * `z0m_se`: Only if `method = wind_profile`: Standard Error of the median for z0m (m)

# References

  * Choudhury, B. J., Monteith J_L., 1988: A four-layer model for the heat budget of homogeneous land surfaces. Q. J. R. Meteorol. Soc. 114, 373-398.
  * Shaw, R. H., Pereira, A., 1982: Aerodynamic roughness of a plant canopy:  a numerical experiment. Agricultural Meteorology, 26, 51-65.

# See also

[`wind_profile`](@ref)

```jldoctest; output = false
using DataFrames
# estimate d and z0m from canopy height for a dense (LAI=5) and open (LAI=2) canopy
zh = 25.0
roughness_parameters(RoughnessCanopyHeightLAI(),zh,5)
roughness_parameters(RoughnessCanopyHeightLAI(),zh,2)   
   
# fix d to 0.7*zh and estimate z0m from the wind profile
df = DataFrame(
  Tair=[25.0,25.0,25.0],pressure=100.0,wind=[3.0,4.0,5.0],
  ustar=[0.5,0.6,0.65],H=200.0)
roughness_parameters(Roughness_wind_profile(),df;zh,zr=40,d=0.7*zh)

# assume d = 0.8*zh
rp = roughness_parameters(Roughness_wind_profile(),df;zh,zr=40,d=0.8*zh)
≈(rp.z0m, 0.55, rtol=0.1)
# output
true
```
