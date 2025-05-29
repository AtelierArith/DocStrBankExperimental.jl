```
IdealClarifier(states; f_ns = 0, name)
```

An Ideal Clarifier. This system defines an ideal clarifier. It is a static system that ensures mass conservation and ideally  settles all particulate compounds: a parameter for the unsettlable fraction of solids can be given. The flow rates of the outflows (effluent or sludge) are to be provided by the following systems, e.g. using a [`FlowPump`](@ref) system.

# Parameters:

  * `states`: The components that the clarifier should have
  * `f_ns`: The unsettlable fraction of solids

# Connectors:

  * `inflow`: The inflow of the IdealClarifier
  * `effluent`: The effluent of the IdealClarifier
  * `sludge`: The the sludge outflow of the IdealClarifier
