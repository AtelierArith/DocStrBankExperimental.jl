```
FlowPump(state; flowrate=nothing, name)
```

A component modeling a flow pump. It models an ideal flow pump, where a provided flow is pumped through.

The `FlowPump` has one inflow and one outflow and it merely specifies the flow passing through.

!!! warning
    If the flow pumped by a `FlowPump` does not match what is incoming, the flow will need to find another way.  This can either be that the flow takes another route (through a [`FlowSeparator`](@ref)), or that it is  accumulated/depleted in a previous system that can do so (i.e. has a variable volume). If none of this is possible, the created system can not be successfully simulated, as the equations will be inconsistent.


!!! note
    The `FlowPump` does not split the flow in any way. If you intend to extract a sidestream from a main flow, use a combination of a [`FlowSeparator`](@ref) (to split the flows) and a `FlowPump`  at one outlet (to specify the flowrate there).


# Parameters:

  * `states`: The components in the flows
  * `flowrate`: The flowrate to pump. If `nothing` (default) an input is added for setting it dynamically

# Connectors:

  * `inflow`: The inflow of the Pump
  * `outflow`: The outflow of the Pump
  * `q_pumped`: **Optional**: [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref) to provide the pumped flow rate. Added only if the parameter `flowrate` is `nothing`, otherwise the flowrate is considered fixed at the given value.
