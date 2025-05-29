```
mcpropagate(mm::MeasurementModel, inputs::UncertainValues, n::Int, parallel::Bool=true, rng::AbstractRNG = Random.GLOBAL_RNG)::UncertainValues
```

Propagate the `inputs` through the `MeasurementModel` using a MonteCarlo algorithm in which the inputs are assumed to be represented by a `MvNormal` distribution with covariance from `inputs`.  Performs 'n' iterations and multi-thread if `parallel=true`.
