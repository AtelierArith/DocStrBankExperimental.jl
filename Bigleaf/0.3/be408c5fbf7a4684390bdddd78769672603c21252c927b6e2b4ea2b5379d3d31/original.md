```
add_Gb(Gb_h::Union{Missing,Number}, Sc::Vararg{Pair,N}; constants)
add_Gb!(df::AbstractDataFrame, Sc::Vararg{Pair,N}; Gb_h = df.Gb_h, kwargs...)
```

compute boundary layer conductance for additional quantities for given Schmidt-numbers

# Arguments

  * `Gb_h`     : Boundary layer conductance for heat transfer (m s-1)
  * `Sc`       : several `Pair{Symbol,Number}` Output name and Schmidt number of               additional conductances to be calculated
  * `df`       : DataFrame to add output columns

optional

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries 

      * `Pr` - Prandtl number

# Details

Boundary layer conductance for other quantities x is calculated  based on boundary layer for heat transfer as (Hicks et al. 1987):

$Gb_x = Gb_h / (Sc_x / Pr)^{0.67}$

where `Sc_x` is the Schmidt number of quantity x, and Pr is the Prandtl number (0.71).

# Value

a NameTuple or `df` with keys `Gb_x` where `x` are the keys in `Sc` and  corresponding boundary layer conductances (m s-1).

# Examples

```jldoctest; output=false
using DataFrames
df = DataFrame(Gb_h=[0.02, missing, 0.055])
add_Gb!(df, :O2 => 0.84, :CH4 => 0.99)
propertynames(df)[2:3] == [:Gb_O2, :Gb_CH4]
# output
true
```
