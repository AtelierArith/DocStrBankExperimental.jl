```
Sensor(states, sensed; name)
```

A component to provide certain states as real outputs. Is convenient if certain states are to be extracted for control.

!!! note
    This system does not include any measurement model nor noise. It simply gets the information out.


# Parameters:

  * `states`: The components in the Flows
  * `sensed`: The sources defining the values. Either a vector or a single value
  * `flowrate`: Named parameter to specify the flowrate. Set to `nothing` if included in the states.

# Connectors:

  * `inflow`: The inflow to the sensor
  * `outflow`: The outflow of the sensor (equal to the inflow)
  * one exogenous_output for each sensed state. Named after the state.
