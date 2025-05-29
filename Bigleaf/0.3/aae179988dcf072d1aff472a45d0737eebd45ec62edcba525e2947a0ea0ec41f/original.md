```
compute_Gb!(df::AbstractDataFrame, approach; kwargs...)
```

Estimate boundary layer conductance.

# Arguments

  * `df`       : DataFrame with required variables (depend on approach)
  * `approach` : one of

      * `Thom1972()`: see [`Gb_Thom`](@ref)
      * `Choudhury1988()`: see [`Gb_Choudhury`](@ref)
      * `Su2001()`: see [`Gb_Su`](@ref)
      * `ConstantKB1()`: see [`Gb_constant_kB1`](@ref)

The different approaches require different variables to be present in `df` and different keyword arguments.

# Value

updated DataFrame `df` with the following columns:

  * `Gb_h`: Boundary layer conductance for heat transfer (m s-1)

To subsequently derived quantities see

  * [`compute_Gb_quantities`](@ref) for Resistance, kB^(-1) constant, and CO2 conductance
  * [`add_Gb!`](@ref) for conductances of other species given their Schmidt numbers.

# See also

[`Gb_Thom`](@ref), [`Gb_Choudhury`](@ref), [`Gb_Su`](@ref), [`Gb_constant_kB1`](@ref),  [`aerodynamic_conductance!`](@ref)

```jldoctest; output = false
using DataFrames
df = DataFrame(wind=[3,4,5], ustar=[0.5,0.6,0.65]) 
compute_Gb!(df, Thom1972())
≈(df.Gb_h[1], 0.102, rtol=1e-2)
# output
true
```
