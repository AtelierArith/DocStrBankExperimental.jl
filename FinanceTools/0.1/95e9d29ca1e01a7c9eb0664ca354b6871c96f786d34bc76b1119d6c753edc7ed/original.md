Calculates the fractional difference of a vector of numbers.

# Arguments

  * `d::Real` : Order of difference, applies the n'th order of fractional difference to the series. Integer orders result in the same as the lag operator.
  * `cutoff::Real=1e-3` : The minimum value of a term in the binomial weights, lower values will result in a more precise result with a higher computatinal cost.

#### Example

```julia
julia> fracdiff([0.:10.;], 0.5)

# This results in:
11-element Vector{Float64}:
 -4.1236855200362954e-16
  1.0000000000000002
  1.5
  1.8750000000000002
  2.1874999999999996
  2.4609375
  2.707031249999998
  2.9326171874999987
  3.1420898437499987
  3.3384704589843737
  3.523941040039061
```
