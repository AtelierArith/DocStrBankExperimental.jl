```
rf_abc_model_choice(models, summary_stats_observations,
                    summary_stats_func::Function, N_ref::Int;
                    k::Int = N_ref, distance_func::Function = (x,y) -> 1, 
                    hyperparameters_range::Dict)
```

Run the Random Forest Approximate Bayesian Computation model choice method.

The mandatory arguments are:

  * `models` is a list of objects inherited from `Model` or `ParametricModel`,
  * `summary_stats_observations` are the summary statitics of the observations
  * `N_ref`: the number of samples in the reference table.
  * `summary_stats_func::Function`: the function that computes the summary statistics over a model simulation.

The optional arguments are:

  * `models_prior`: the prior over the models (by default: discrete uniform distribution)
  * `k`: the k nearest samples from the observations to keep in the reference table (by default: k = N_ref)
  * `distance_func`: the distance function, has to be defined if k < N_ref
  * `hyperparameters_range`: a dict with the hyperparameters range values for the cross validation fit of the    Random Forest (by default: `Dict(:n_estimators => [200], :min_samples_leaf => [1], :min_samples_split => [2])`).   See scikit-learn documentation of RandomForestClassifier for the hyperparameters name.

The result is a `RandomForestABC` object with fields:

  * `reference_table` an AbcModelChoiceDataset that corresponds to the reference table of the algorithm,
  * `clf` a random forest classifier (PyObject from scikit-learn),
  * `summary_stats_observations` are the summary statitics of the observations
  * `estim_model` is the underlying model of the observations inferred with the RF-ABC method.
