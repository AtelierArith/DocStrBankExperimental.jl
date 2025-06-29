```
heat_transfer(f::Fluid, t::Tube)
```

Computes the heat transfer coefficient of a `fluid``flowing through a`tube`.

# Arguments

  * `f::Fluid`: the fluid flowing through the tube
  * `t::Tube`: the tube through which the fluid flows

# Returns

  * `DynamicQuantity.AbstractQuantity`: the heat transfer coefficient of the fluid flowing through the tube
