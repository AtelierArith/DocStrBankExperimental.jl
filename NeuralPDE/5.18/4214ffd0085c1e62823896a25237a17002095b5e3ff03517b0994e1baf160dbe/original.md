```
QuasiRandomTraining(points; bcs_points = points,
                            sampling_alg = LatinHypercubeSample(), resampling = true,
                            minibatch = 0)
```

A training strategy which uses quasi-Monte Carlo sampling for low discrepancy sequences that accelerate the convergence in high dimensional spaces over pure random sequences.

## Positional Arguments

  * `points`:  the number of quasi-random points in a sample

## Keyword Arguments

  * `bcs_points`: the number of quasi-random points in a sample for boundary conditions (by default, it equals `points`),
  * `sampling_alg`: the quasi-Monte Carlo sampling algorithm,
  * `resampling`: if it's false - the full training set is generated in advance before training, and at each iteration, one subset is randomly selected out of the batch. If it's true - the training set isn't generated beforehand, and one set of quasi-random points is generated directly at each iteration in runtime. In this case, `minibatch` has no effect.
  * `minibatch`: the number of subsets, if `!resampling`.

For more information, see [QuasiMonteCarlo.jl](https://docs.sciml.ai/QuasiMonteCarlo/stable/).
