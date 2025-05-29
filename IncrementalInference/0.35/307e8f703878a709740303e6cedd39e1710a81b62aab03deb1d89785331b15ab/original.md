```julia
calcFactorResidual(dfgfct, args; ccw)

```

Helper function for evaluating factor residual functions, by adding necessary `CalcFactor` wrapper.

Notes

  * Factor must already be in a factor graph to work
  * Will not yet properly support all multihypo nuances, more a function for testing
  * Useful for debugging a factor.

Example

```julia
fg = generateGraph_Kaess()

residual = calcFactorResidual(fg, :x1x2f1, [1.0], [0.0], [0.0])
```

Related

[`calcFactorResidualTemporary`](@ref), [`_evalFactorTemporary!`](@ref), [`approxConvBelief`](@ref)
