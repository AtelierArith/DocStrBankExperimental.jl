```
 dmuEfficiencyDual(I₀,O₀,I,O)
```

Compute the efficiency score for a DMU using vanilla Data Envelope Analysis in the dual representation using the two pass method.

## Parameters:

  * `I₀`: This DMU inputs (nI)
  * `O₀`: This DMU outputs (n0)
  * `I`: All DMUs inputs (nDMU x nI)
  * `O`: All DMUs outputs (nDMU x n0)

## Returns:

  * A named tuple with:

      * `computed`: a boolean to indicase wheter the underlying optimisation succeeded
      * `eff`: a boolean to indicate if the DMU is efficient or not
      * `obj`: a scalar representing the efficiency score of the DMU
      * `λ`
      * `θ`
      * `dualsI`
      * `dualsO`
      * `s⁻`
      * `s⁺`
