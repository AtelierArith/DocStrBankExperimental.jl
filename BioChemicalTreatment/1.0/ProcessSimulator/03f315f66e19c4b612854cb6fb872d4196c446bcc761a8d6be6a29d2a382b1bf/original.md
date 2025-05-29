```
CSTR(V, states; initial_states = nothing, name)
```

A Continuously Stirred Tank Reactor (CSTR). This system defines the mass flow of a CSTR without any reactions. The reactions are to be supplied from an external system. The mass transfer of an given component $C$ in a CSTR with volume $V$ and flow rate $q$ is defined as:     $\frac{dC}{dt} = (C_{in} - C) * \frac{q}{V} + r_C$ where $r_C$ is the externally supplied reaction rate corresponding to the component.

# Parameters:

  * `V`: The volume of the CSTR
  * `states`: The components that the CSTR should have and for which the mass transfer is defined
  * `initial_states`: The initial concentrations in the CSTR

# States:

  * One state for each component defined by the `states` parameter

# Connectors:

  * `inflow`: The inflow of the CSTR
  * `outflow`: The outflow of the CSTR
  * `state`: The current values of all states in the CSTR
  * `rates`: Input for the reaction rates for each state
