```
NearSourceSaturationParameters
```

Struct for near-source saturation parameters. Mimic structure of the `GeometricSpreadingParameters` struct. Holds fields:

  * `mRefi` reference magnitudes
  * `hconi` constrained coefficients, not free for AD purposes
  * `hvari` variable coefficients, free for AD purposes
  * `hfree` is a vector of `Bool` instances, or a `BitVector` indicating which parameters are constant or variable
  * `exponent` is the exponent used within equivalent point-source distance calculations: $r_{ps} = \left[r_{rup}^n + h(m)^n\right]^{1/n}$
  * `model` is a symbol defining the type of saturation model:

      * `:BT15` is Boore & Thompson (2015)
      * `:YA15` is Yenier & Atkinson (2015)
      * `:CY14` is average Chiou & Youngs (2014)
      * `:None` returns zero saturation length
      * `:ConstantConstrained` is a fixed saturation length not subject to AD operations
      * `:ConstantVariable` is a fixed saturation length that is subject to AD operations (i.e., is a `<:Dual`)
