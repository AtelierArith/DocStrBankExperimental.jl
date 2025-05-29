```
function AddNoise(G::GraphSig; SNR::Float64=Float64(1.24), noisetype::String = "gaussian")
```

Add noise to the data of a GraphSig object

### Input Arguments

  * `G::GraphSig`: a GraphSig object
  * `SNR`: the SNR that the noisy signal should have
  * `noisetype`: the type of noise: Gaussian (default) or Poisson

### Output Argument

  * `G::GraphSig`: the GraphSig object with added noise
  * `sigma`: the standard deviation of the noise
