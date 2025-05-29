```
Celani{D} <: AbstractMicrobe{D}
```

Model of chemotactic bacterium using the response kernel from 'Celani and Vergassola (2010) PNAS', extracted from experiments on E. coli.

Sensing noise (not present in the original model) is customarily introduced through the molecular counting noise formula by Berg and Purcell, and can be tuned through a `chemotactic_precision` factor inspired by 'Brumley et al. (2019) PNAS' (defaults to 0, i.e. no noise).

Default parameters:

  * `motility = RunTumble(0.67, [30.0], Isotropic(D), 0.1)
  * `state = 0`
  * `rotational_diffusivity = 0.26` rad²/s
  * `gain = 50.0`
  * `memory = 1` s
  * `radius = 0.5` μm
