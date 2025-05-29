```
BrownBerg{D} <: AbstractMicrobe{D}
```

Model of chemotactic E.coli from 'Brown and Berg (1974) PNAS'

Default parameters:

  * `motility = RunTumble(0.67, [30.0], Isotropic(D), 0.1)`
  * `rotational_diffusivity = 0.035` rad²/s coefficient of brownian rotational diffusion
  * `radius = 0.5` μm equivalent spherical radius of the microbe
  * `state = 0.0` corresponds to 'weighted dPb/dt' in the paper
  * `gain = 660` s
  * `receptor_binding_constant = 100` μM
  * `memory = 1` s
