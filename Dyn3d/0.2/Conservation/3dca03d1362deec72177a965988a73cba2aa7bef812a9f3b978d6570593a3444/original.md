```
force!(dict,bd,λ,k)
```

  * `dict` : structure of terms in the energy conservation. Includes keys of   "mlag", "mlag*temp", "mgra", "mgra*temp", "mkin"
  * `bd` : current BodyDyn structure
  * `λ` : force by body on the constrained dof of joints
  * `k` : k-1 represents the current the stage in rk scheme

Computes the force by lagrangian multipliers in inertia frame at one stage in a timestep of rk scheme if the body-joint system is under active prescribed motion. Also computes gravity force at one stage. This function needs to be called at every stage in RK scheme.
