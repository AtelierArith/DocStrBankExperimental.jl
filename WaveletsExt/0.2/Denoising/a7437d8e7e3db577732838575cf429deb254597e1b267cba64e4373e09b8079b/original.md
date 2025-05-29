```
RelErrorShrink(th, t) <: DNFT
```

Relative Error Shrink method used in their paper "Efficient Approximation and Denoising of Graph Signals using the Multiscale Basis Dictionary" for IEEE Transactions on Signal and Information Processing over Networks, Vol 0, No. 0, 2016.

# Attributes

  * `th::Wavelets.Threshold.THType`: (Default: `Wavelets.HardTH()`) Threshold type.
  * `t::AbstractFloat`: (Default: 1.0) Threshold size.

# Examples

```julia
using Wavelets, WaveletsExt

RelErrorShrink()                    # Using default th and t values
RelErrorShrink(SoftTH())            # Using default t value
RelErrorShrink(HardTH(), 0.5)       # Using user input th and t values
```

**See also:** [`SureShrink`](@ref), [`VisuShrink`](@ref)
