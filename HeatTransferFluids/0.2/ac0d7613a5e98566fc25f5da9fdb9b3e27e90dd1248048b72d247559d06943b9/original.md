```
nusselt_number(f::Fluid, t::Tube)
```

Computes the Nusselt number of a `fluid` flowing through a `tube`.

Depending on the regime (laminar or turbulent), different formula have to be used to compute the Nusselt number. For the intermediate region, we perform a linear interpolation between the laminar and turbulent regimes. See VDI Heat Atlas, p. 696 for details.

# Arguments

  * `f::Fluid`: the fluid flowing through the tube
  * `t::Tube`: the tube through which the fluid flows

# Returns

  * `Float`: the Nusselt number of the fluid flowing through the tube
