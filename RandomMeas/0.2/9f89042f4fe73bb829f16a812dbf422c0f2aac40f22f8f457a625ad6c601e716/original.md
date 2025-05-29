```
get_overlap(prob1::MeasurementProbability, prob2::MeasurementProbability) -> Float64
```

Compute the weighted overlap  `\2^N sum_s (-2)^{-D[s,s']}P(s)P(s')]` by sequentially applying the Hamming tensor to each qubit index and contracting with the second probability tensor.

# Arguments

  * `prob1::MeasurementProbability`: The first Born probability tensor representing quantum state `rho1`.
  * `prob2::MeasurementProbability`: The second Born probability tensor representing quantum state `rho2`.

# Returns

  * `weighted_overlap::Float64`: The computed trace `Tr(rho1 rho2)` scaled appropriately..

# Example

```julia
using ITensors

# Assume prob1 and prob2 are predefined MeasurementProbabilities
overlap = get_overlap(prob1, prob2)
println("Overlap: ", overlap)
```
