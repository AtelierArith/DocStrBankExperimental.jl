```
BatchReactor(states; initial_states = nothing, name)
```

A Batch Reactor. This system defines the mass transfer of a batch reactor (which is in fact empty). The reactions are to be supplied from an external system. The volume of the tank is not needed, as only concentration is considered and the equation thus independent of the volume. The equations for component $C$ in a Batch reactor is then defined as:     $\frac{dC}{dt} = r_C$ where $r_C$ is the externally supplied reaction rate corresponding to the component.

# Parameters:

  * `states`: The components that the batch reactor should have and for which the mass transfer is defined
  * `initial_states`: The initial concentrations in the batch reactor

# States:

  * One state for each component defined by the `states` parameter

# Connectors:

  * `state`: The current values of all states in the batch reactor
  * `rates`: Input for the reaction rates for each state
