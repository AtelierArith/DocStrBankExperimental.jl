```
SurfacePanel(rtl, rtr, rbl, rbr, rcp, ncp, core_size, chord; kwargs...)
```

Construct and return a vortex ring panel.

# Arguments

  * `rtl`: position of the left side of the top bound vortex
  * `rtr`: position of the right side of the top bound vortex
  * `rbl`: position of the left side of the bottom bound vortex
  * `rbr`: position of the right side of the bottom bound vortex
  * `rcp`: position of the panel control point
  * `ncp`: normal vector at the panel control point
  * `core_size`: finite core size (for use when the finite core smoothing model is enabled)
  * `chord`: panel chord length (for determining unsteady forces)

# Keyword Arguments

  * `rtc`: position of the center of the top bound vortex, defaults to `(rtl+rtr)/2`
  * `rbc`: position of the center of the bottom bound vortex, defaults to `(rbl+rbr)/2`
