```
work!(dict,bd,λ,k)
```

  * `dict` : structure of terms in the energy conservation. Includes keys of   "edam", "edam*temp", "elag", "elag*temp", "ekin", "espr", "egra"
  * `bd` : current BodyDyn structure
  * `λ` : force by body on the constrained dof of joints
  * `k` : k-1 represents the current the stage in rk scheme

Computes the work done by lagrangian multipliers within one stage in a timestep of rk scheme if the body-joint system is under active prescribed motion. Also computes the energy extracted by damper within one stage. This function needs to be called at every stage in RK scheme.
