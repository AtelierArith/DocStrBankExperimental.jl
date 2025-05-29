```
Aeration(; name, k_La=240, S_O_max=8)
```

A component that defines a simple the aeration process using the oxygen transfer coefficient k_L*a and the oxygen saturation concentration.

# Parameters:

  * `k_La` initial oxygen transfer coefficient (default 240 1/d)
  * `S_O_max` the saturation concentration for oxygen (default 8 g/m^3)

# States:

  * `S_O` oxygen

# Connectors

  * `state` The reactor states to connect (only dissolved oxygen)
  * `rate` The calculated rate (dissolved oxygen only)
  * `k_La` The oxygen transfer coefficent. Is a [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref), for usage with the systems from the `ModelingToolkitStandardLibrary` which provides e.g. controllers.
