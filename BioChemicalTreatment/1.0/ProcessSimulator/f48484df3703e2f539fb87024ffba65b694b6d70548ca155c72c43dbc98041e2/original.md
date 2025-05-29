```
Influent(states, sources::Vector; name, flowrate=nothing)
```

A component to provide an influent for a simulation.

There are three possibilities for the source:

  * Numeric constant
  * Function taking a single numeric time argument
  * ODESystem with `source.output` evaluating to a valid [`RealOutput`](@extref ModelingToolkitStandardLibrary.Blocks.RealOutput) port.   All Source blocks from the [`ModelingToolkitStandardLibrary`](https://docs.sciml.ai/ModelingToolkitStandardLibrary/stable/API/blocks/#Source-Blocks)   fulfill this property.

# Parameters:

  * `states`: The components in the Flows
  * `sources`: The vector of sources defining the values.
  * `flowrate`: Named parameter to specify the flowrate. Set to `nothing` if included in the states.

# Connectors:

  * `outflow`: The outflow provided by the `Influent`
