```
FlowSeparator(state; n_out=2, name)
```

A component for separating a single flow into multiple. It is an alias for the `FlowConnector` having only one inflow.

The flow rates along which the flow is to be split have to be provided by the following systems, e.g. a [`FlowPump`](@ref). Connect e.g. a [`FlowPump`](@ref) to all except one outflow, the last one is then already fixed by the mass balance.

# Parameters:

  * `states`: The components in the flows
  * `n_out`: The number of outflows, defaults to 2

# Connectors:

  * `inflow`: The inflow of the `FlowSeparator`
  * `outflow_i`: The i-th outflow of the `FlowSeparator`
