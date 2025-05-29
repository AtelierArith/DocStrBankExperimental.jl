```
informed_init([rng], [T], dims...;
    scaling=0.1, model_in_size, gamma=0.5)
```

Create an input layer for informed echo state networks [^pathak2018].

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the matrix. Should follow `res_size x in_size`.

# Keyword arguments

  * `scaling`: The scaling factor for the input matrix. Default is 0.1.
  * `model_in_size`: The size of the input model.
  * `gamma`: The gamma value. Default is 0.5.

# Examples

[^pathak2018]: Pathak, Jaideep, et al. "Hybrid forecasting of chaotic processes: Using machine learning in conjunction with a knowledge-based model." Chaos: An Interdisciplinary Journal of Nonlinear Science 28.4 (2018).
