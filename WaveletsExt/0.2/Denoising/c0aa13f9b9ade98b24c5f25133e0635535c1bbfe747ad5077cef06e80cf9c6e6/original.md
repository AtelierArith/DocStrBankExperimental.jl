```
SureShrink(xw[, redundant, tree, th])
```

Struct constructor for `SureShrink` based on the signal coefficients `xw`.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: Decomposed signal.
  * `redundant::Bool`: (Default: `false`) Whether the transform type of `xw` is a redundant transform. Autocorrelation and stationary wavelet transforms are examples of redundant transforms.
  * `tree::Union{BitVector, Nothing}`: (Default: `nothing`) The basis tree for decomposing `xw`. Must be provided if `xw` is decomposed using `wpt`, `swpd`, or `acwpd`.
  * `th::Wavelets.Threshold.THType`: (Default: `HardTH()`) Threshold type.

# Returns

`::SureShrink`: SUREShrink object.

# Examples

```julia
SureShrink(xw)                  # `xw` is output of dwt, wpt
SureShrink(xw, true)            # `xw` is output of sdwt, acdwt, swpt, acwpd
SureShrink(xw, true, tree)      # `xw` is output of swpd, acwpd
```

**See also:** [`SureShrink`](@ref), [`surethreshold`](@ref)
