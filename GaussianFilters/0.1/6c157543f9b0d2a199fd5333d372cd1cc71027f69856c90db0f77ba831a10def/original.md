```
run_filter(filter::AbstractFilter, b0::GaussianBelief, action_history::Vector{AbstractVector},
        measurement_history::Vector{AbstractVector})
```

Given an initial belief b0, matched-size arrays for action and measurement histories and a filter, update the beliefs using the filter, and return a vector of all beliefs.
