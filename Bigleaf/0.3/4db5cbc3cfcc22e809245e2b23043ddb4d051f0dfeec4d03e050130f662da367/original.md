```
add_Ga(Gb_h, Ga_m, Sc::Vararg{Pair,N}; constants)
add_Ga!(df::AbstractDataFrame, Sc; Gb_h = df.Gb_h, Ga_m = df.Ga.m, kwargs...)
```

compute additional aerodynamic conductance quantities for given Schmidt-numbers

# Arguments

  * `Gb_h`     : Boundary layer conductance for heat transfer (m s-1)
  * `Ga_m`     : Aerodynamic conductance for momentum (m s-1)
  * `Sc`       : several `Pair{Symbol,Number}` Output name and Schmidt number of               additional conductances to be calculated
  * `df`       : DataFrame to add output columns

optional

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries 

      * `Pr` - Prandtl number

# Details

Aerodynamic conductance is calculated as

$G_{a_x} = 1/(1/G_{a_m} + 1/G_{b_x})$

where `Gb_x` is the Boundary layer conductance for other quantities x is calculated  based on boundary layer for heat transfer, Schmidt-Number, and  Prantl number, as documented in [`add_Gb!`](@ref).

# Value

a NameTuple or `df` with keys `Ga_x` where `x` are the keys in `Sc` and  corresponding aerodynamic conductances (m s-1).

# Examples

```jldoctest; output=false
using DataFrames
df = DataFrame(Gb_h=[0.02, missing, 0.055], Ga_m = 1 ./ [0.03, 0.03, 0.03])
add_Ga!(df, :O2 => 0.84, :CH4 => 0.99)
propertynames(df)[3:4] == [:Ga_O2, :Ga_CH4]
# output
true
```
