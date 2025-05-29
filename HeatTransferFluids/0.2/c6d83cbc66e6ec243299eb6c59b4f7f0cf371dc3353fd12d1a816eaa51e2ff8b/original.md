```
pressure_drop(f::Fluid, t::Tube[; friction])
```

Computes the pressure drop of a `fluid` flowing through a `tube` with a particular `friction`.

See VDI Heat Atlas, p. 1057 for details.

# Arguments

  * `f::Fluid`: the fluid flowing through the tube
  * `t::Tube`: the tube through which the fluid flows

# Keywords

  * `friction::Float`: the friction factor of the fluid flowing through the tube

# Returns

  * `DynamicQuantities.AbstractQuantity`: the pressure drop of the fluid flowing through the tube
