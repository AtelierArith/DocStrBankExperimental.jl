```
FlowUnifier(state; n_in=2, name)
```

A component for unifying multiple flows into a single one. It is an alias for the `FlowConnector` having only one outflow.

# Parameters:

  * `states`: The components in the flows
  * `n_in`: The number of inflows, defaults to 2

# Connectors:

  * `inflow_i`: The i-th inflow of the `FlowUnifier`
  * `outflow`: The outflow of the `FlowUnifier`
