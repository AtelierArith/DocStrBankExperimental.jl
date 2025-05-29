```
sample(bpc::CuBitsProbCircuit, num_samples::Int, num_rand_vars::Int, types; rng=default_rng())
```

Generate `num_samples` from the joint distribution of the circuit without any conditions. Samples are genearted on the GPU. 

  * `bpc`: Circuit on gpu (CuBitProbCircuit)
  * `num_samples`: how many samples to generate
  * `num_rand_vars`: number of random variables in the circuit
  * `types`: Array of possible input types
  * `rng`: (Optional) Random Number Generator

The size of returned Array is `(num_samples, 1, size(data, 2))`.
