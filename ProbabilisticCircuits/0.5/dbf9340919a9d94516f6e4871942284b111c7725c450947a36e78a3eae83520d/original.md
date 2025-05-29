```
sample(bpc::CuBitsProbCircuit, num_samples, data::CuMatrix; rng=default_rng())
```

Generate `num_samples` for each datapoint in `data` from the joint distribution of the circuit conditioned on the `data`. Samples are generated using GPU. 

  * `bpc`: Circuit on gpu (CuBitProbCircuit)
  * `num_samples`: how many samples to generate
  * `rng`: (Optional) Random Number Generator

The size of returned CuArray is `(num_samples, size(data, 1), size(data, 2))`.
