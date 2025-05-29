```
Brumley{D} <: AbstractMicrobe{D}
```

Model of chemotactic bacterium from 'Brumley et al. (2019) PNAS'. The model is optimized for simulation of marine bacteria and accounts for the presence of (gaussian) sensing noise in the chemotactic pathway.

Default parameters:

  * `motility = RunReverseFlick(0.45, [46.5], 0.45, [46.5])`
  * `state = 0.0` → 'S'
  * `rotational_diffusivity = 0.035` rad²/s
  * `memory = 1.3` s → 'τₘ'
  * `gain_receptor = 50.0` μM⁻¹ → 'κ'
  * `gain = 50.0` → 'Γ'
  * `chemotactic_precision = 6.0` → 'Π'
  * `radius = 0.5` μm → 'a'
