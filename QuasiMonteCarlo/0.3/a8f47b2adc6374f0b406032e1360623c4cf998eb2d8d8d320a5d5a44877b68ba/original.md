```julia
DesignMatrix(n, d, sample_method::DeterministicSamplingAlgorithm, num_mats, T = Float64)
```

Create an iterator for doing multiple i.i.d. randomization over QMC sequences where

  * `num_mats` is the lenght of the iterator
  * `n` is the number of points to sample.
  * `d` is the dimensionality of the point set in `[0, 1)ᵈ`,
  * `sample_method` is the quasi-Monte Carlo sampling strategy used to create a deterministic point set `out`.
  * `T` is the `eltype` of the point sets. For some QMC methods (Faure, Sobol) this can be `Rational`

It is now compatible with all scrambling methods and shifting. One can also use it with `Distributions.Sampleable` or `RandomSample`.
