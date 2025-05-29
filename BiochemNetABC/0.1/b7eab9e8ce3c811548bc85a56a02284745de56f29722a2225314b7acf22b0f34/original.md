```
abc_model_choice_dataset(models, models_prior,
                         summary_stats_observations,
                         summary_stats_func::Function, distance_func::Function,
                         k::Int, N_ref::Int; dir_results::Union{Nothing,String} = nothing)
```

Creates a reference table for ABC model choice.

The mandatory arguments are:

  * `models` is a list of objects inherited from `Model` or `ParametricModel`,
  * `models_prior`: the prior over the models (by default: discrete uniform distribution)
  * `summary_stats_observations` are the summary statitics of the observations,
  * `summary_stats_func::Function`: the function that computes the summary statistics over a model simulation,
  * `distance_func`: the distance function over the summary statistics space,
  * `N_ref`: the number of samples in the reference table,
  * `k`: the k nearest samples from the observations to keep in the reference table (k < N_ref).

The result is a `AbcModelChoiceDataset` with fields:

  * `summary_stats_matrix`: the (N*stats, N*ref) features matrix. Accessible via `.X`.
  * `summary_stats_observations`: the observations used for simulating the dataset.
  * `models_indexes`: the labels vector. Accessible via `.y`.

If specified, `dir_results` is the directory where the summary statistics matrix and associated models are stored (CSV).
