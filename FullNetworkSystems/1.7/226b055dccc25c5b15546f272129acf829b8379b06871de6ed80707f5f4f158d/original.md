```julia
struct Branch
```

Type for static branch attributes.  Branches may have between 0 and 2 break points which is why the `break_points` and `penalties` fields contain variable length `Tuple`s.

Fields:

  * `name::InlineStrings.String31`: Branch long name
  * `to_bus::InlineStrings.String15`: Name of the bus the branch goes to
  * `from_bus::InlineStrings.String15`: Name of the bus the branch goes from
  * `rate_a::Float64`: Power flow limit for the base case (pu)
  * `rate_b::Float64`: Power flow limit for contingency scenario (pu)
  * `is_monitored::Bool`: Boolean defining whether the branch is monitored
  * `break_points::Tuple{Float64, Float64}`: Break points of the branch. Branches can have 0, 1, or 2 break points. Zeros indicate no break point

  * `penalties::Tuple{Float64, Float64}`: Price penalties for each of the break points of the branch ($)
  * `resistance::Float64`: Resistance of the branch (pu)
  * `reactance::Float64`: Reactance of the branch (pu)
  * `is_transformer::Bool`: Boolean indicating whether the branch is a transformer
  * `tap::Union{Missing, Float64}`: Ratio between the nominal winding one and two voltages of the transformer
  * `angle::Union{Missing, Float64}`: Phase shift angle (radians)
