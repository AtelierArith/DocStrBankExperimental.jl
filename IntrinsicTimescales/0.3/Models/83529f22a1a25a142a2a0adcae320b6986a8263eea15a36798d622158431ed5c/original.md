```
check_model_inputs(data, time, fit_method, summary_method, prior, acwtypes, distance_method)
```

Validate inputs for timescale model construction.

# Arguments

  * `data`: Input time series data
  * `time`: Time points corresponding to the data
  * `fit_method`: Fitting method (:abc, :advi)
  * `summary_method`: Summary statistic type (:psd or :acf)
  * `prior`: Prior distribution(s) for parameters
  * `acwtypes`: Types of ACW analysis
  * `distance_method`: Distance metric type (:linear or :logarithmic)

# Throws

  * `ArgumentError`: If any inputs are invalid or incompatible
