```
rf_abc_model_choice(abc_trainset;
                    k::Int = N_ref, distance_func::Function = (x,y) -> 1, 
                    hyperparameters_range::Dict)
```

Run the Random Forest Approximate Bayesian Computation model choice method with an already simulated dataset.

The mandatory arguments are:

  * `abc_trainset`: an already simulated dataset with ``abc_model_choice_dataset`

The optional arguments are:

  * `hyperparameters_range`: a dict with the hyperparameters range values for the cross validation fit of the    Random Forest (by default: `Dict(:n_estimators => [200], :min_samples_leaf => [1], :min_samples_split => [2])`).   See scikit-learn documentation of RandomForestClassifier for the hyperparameters name.

The result is a `RandomForestABC` object with fields:

  * `reference_table` an AbcModelChoiceDataset that corresponds to the reference table of the algorithm,
  * `clf` a random forest classifier (PyObject from scikit-learn),
  * `summary_stats_observations` are the summary statitics of the observations
  * `estim_model` is the underlying model of the observations inferred with the RF-ABC method.
