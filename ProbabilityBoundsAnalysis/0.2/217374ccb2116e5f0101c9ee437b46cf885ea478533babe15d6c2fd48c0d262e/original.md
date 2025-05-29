```
mutable struct pbox <: AbstractPbox
```

Basic type used in Probability Bounds Analysis. A set of probability distributions defined by an upper (u) and lower (d/down) cdf, interval bounds on mean and variance and distibution shape (eg. Normal).

If partial information is given (eg, no bounds on moments), the other properties are determined from provided information.

# Constructors

  * `pbox()                     => Vacous case`
  * `pbox(u :: Real)            => Scalar case`
  * `pbox(u :: Real, d :: Real) => Interval case`
  * `pbox(u :: Array{<:Real}, d :: Array{<:Real}, shape :: String, ml :: Real, mh :: Real, vl :: Real, vh :: Real)`

where ml/mh are the lower/upper mean, and vl/vh are the lower/upper variance.

See also: [`mean`](@ref), [`var`](@ref), [`uniform`](@ref), [`normal`](@ref), [`conv`](@ref), [`copula`](@ref)
