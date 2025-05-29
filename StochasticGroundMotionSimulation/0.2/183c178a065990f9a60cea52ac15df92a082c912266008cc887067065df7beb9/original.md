```
GeometricSpreadingParameters
```

Struct for geometric spreading parameters. Holds fields:

  * `Rrefi` are reference distances, these are `<:Real` but will generally be `Float64` values
  * `γconi` are constant spreading rates, meaning that they will not be free for AD purposes
  * `γvari` are variable spreading rates, meaning that they can be represented as `Dual` numbers for AD
  * `γfree` is a vector of `Bool` instances, or a `BitVector` that indicates which segments are constant or variable. Variable spreading rates are given `1` or `true`
  * `model` is a symbol defining the type of spreading model `:Piecewise`, `:CY14`, `:CY14mod`
