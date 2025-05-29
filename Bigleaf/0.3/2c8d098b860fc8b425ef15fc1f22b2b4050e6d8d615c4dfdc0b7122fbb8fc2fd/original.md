```
aerodynamic_conductance!(df; 
  Gb_model = Thom1972(), Ram_model = ResistanceWindZr(),
  zr=nothing, zh=nothing, d = isnothing(zh) ? nothing : 0.7*zh,
  ...
  )
```

Bulk aerodynamic conductance, including options for the boundary layer conductance formulation and stability correction functions.

# Arguments

  * `df`: DataFrame with columns

      * `ustar`     : Friction velocity (m s-1)
      * `wind`      : Wind speed at sensor height (m s-1)
  * `Gb_model`  : model for computing boundary layer conductance (see [`compute_Gb!`](@ref))
  * `Ram_model` : model for computing aerodynamic resistance (see [`compute_Ram`](@ref))
  * `zh`        : canopy height (m)
  * `zr`        : Instrument (reference) height (m)

Further required columns of `df` and keyword argument depend on `Gb_model`   (see [`compute_Gb!`](@ref)) and `Ram_model` (see [`compute_Ram`](@ref)).

If only columns `ustar` and `wind` are available, use default models  (`Thom1972()` and `ResistanceWindZr()`).

# Details

Aerodynamic conductance for heat (Ga_h) is calculated as:

$Ga_h = 1 / (Ra_m + Rb_h)$

where $Ra_m$ is the aerodynamic resistance for momentum and $Rb_h = 1/Gb_h$ the  (quasi-laminar) canopy boundary layer resistance ('excess resistance') for heat.

`Ra_m` is computed and described with [`compute_Ram`](@ref) using model `Ram_model`.

`Rb_h` is computed and described with 1/[`compute_Gb!`](@ref) using a given `Gb_model`.

# Value

combined results of [`compute_Gb!`](@ref) and 

  * `Ra_m`: Aerodynamic resistance for momentum transfer (s m-1)
  * `Ga_m`: Aerodynamic conductance for momentum transfer (m s-1)
  * `Ga_h`: Aerodynamic conductance for heat transfer (m s-1)
  * `Ra_h`: Aerodynamic resistance for heat transfer (s m-1)
  * `Ga_CO2`: Aerodynamic conductance for CO2 transfer (m s-1)
  * `z0h`: roughness length for heat (m)

# Note

The roughness length for water and heat (z0h) is computed by [`roughness_length_heat`](@ref).

TODO check Input variables such as LAI, Dl, or zh can be either constants, or vary with time, i.e. are vectors of the same length as `df`.

Note that boundary layer conductance to water vapor transfer (`Gb_w`) is often  assumed to equal `Gb_h`. This assumption is also made in `Bigleaf.jl`, for  example in the function [`surface_conductance`](@ref).

If the roughness length for momentum (`z0m`) is not provided as input, it is estimated  using [`roughness_parameters`](@ref), which estimates a single `z0m`  value for the entire time period. If a varying `z0m` value  (e.g. across seasons or years) is required, `z0m` should be provided as input argument.

# Examples

```jldoctest; output = false
using DataFrames
df = DataFrame(Tair=25.0,pressure=100.0,wind=[3.0,4,5],
  ustar=[0.5,0.6,0.65],H=[200.0,230,250])   
# simple calculation of Ga  
aerodynamic_conductance!(df;Gb_model=Thom1972()) 
# calculation of Ram using a model derived from the logarithmic wind profile
aerodynamic_conductance!(df;Gb_model=Thom1972(),Ram_model = ResistanceWindProfile(), 
  zr=40,zh=25,d=17.5,z0m=2) 
# simple calculation of Ga, but a physically based canopy boundary layer model
aerodynamic_conductance!(df,Gb_model=Su2001(),
  zr=40,zh=25,d=17.5,Dl=0.05,N=2,fc=0.8)
all(isfinite.(df.psi_h))
# output
true
```
