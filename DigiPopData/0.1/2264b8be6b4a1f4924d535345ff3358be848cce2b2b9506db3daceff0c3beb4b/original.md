```
get_loss(simulated::DataFrame, metric_bindings::Vector{MetricBinding}) -> Float64
```

Calculate the loss for a given set of metric bindings and a simulated DataFrame. The function iterates over the metric bindings, selecting the relevant data from the simulated DataFrame  based on the scenario and endpoint specified in each binding. It then computes the loss using the `mismatch`  function defined in the metric.

## Arguments

  * `simulated::DataFrame`: A DataFrame containing the simulated data.
  * `metric_bindings::Vector{MetricBinding}`: A vector of `MetricBinding` objects, each containing a scenario,

endpoint, and metric.
