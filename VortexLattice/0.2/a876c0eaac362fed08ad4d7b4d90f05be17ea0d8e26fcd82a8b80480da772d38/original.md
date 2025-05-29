```
body_forces_history(system, surface_history, property_history; frame=Body())
```

Return the body force coefficients `CF`, `CM` at each time step in `property_history`.

# Arguments:

  * `system`: Object of type [`System`](@ref) which holds system properties
  * `surface_history`: Vector of surfaces at each time step, where each surface is  represented by a matrix of surface panels (see [`SurfacePanel`](@ref)) of shape  (nc, ns) where `nc` is the number of chordwise panels and `ns` is the number  of spanwise panels
  * `property_history`: Vector of surface properties for each surface at each  time step, where surface properties are represented by a matrix of panel  properties (see [`PanelProperties`](@ref)) of shape (nc, ns) where `nc` is  the number of chordwise panels and `ns` is the number of spanwise panels

# Keyword Arguments

  * `frame`: frame in which to return `CF` and `CM`, options are [`Body()`](@ref) (default), [`Stability()`](@ref), and [`Wind()`](@ref)`
