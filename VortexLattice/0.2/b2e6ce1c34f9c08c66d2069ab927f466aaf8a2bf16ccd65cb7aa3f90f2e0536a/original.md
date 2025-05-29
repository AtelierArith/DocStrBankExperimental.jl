```
PanelProperties
```

Panel specific properties calculated during the vortex lattice method analysis.

**Fields**

  * `gamma`: Vortex ring circulation strength, normalized by the reference velocity
  * `velocity`: Local velocity at the panel's bound vortex center, normalized by  the reference velocity
  * `cfb`: Net force on the panel's bound vortex, as calculated using the  Kutta-Joukowski theorem, normalized by the reference dynamic pressure and area
  * `cfl`: Force on the left bound vortex from this panel's vortex ring, as  calculated by the Kutta-Joukowski theorem, normalized by the reference  dynamic pressure and area
  * `cfr`: Force on the right bound vortex from this panel's vortex ring, as  calculated by the Kutta-Joukowski theorem, normalized by the reference  dynamic pressure and area
  * `velocity_from_streamwise`: Local velocity at the panel's bound vortex center  excluding the induced velocity from the bound vorticies, not normalized
