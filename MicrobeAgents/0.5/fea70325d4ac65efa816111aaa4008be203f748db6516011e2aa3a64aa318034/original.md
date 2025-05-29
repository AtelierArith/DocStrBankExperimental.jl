```
Xie{D} <: AbstractMicrobe{D}
```

Model of chemotactic bacterium adapted from 'Xie et al. (2019) Biophys J'. The model is developed based on experimental measurements of the chemotactic response function in the marine bacterium V. alginolyticus. The peculiarity of the model is the presence of distinct parameters for the forward and backward swimming states.

Sensing noise (not present in the original model) is customarily introduced through the molecular counting noise formula by Berg and Purcell, and can be tuned through a `chemotactic_precision` factor inspired by 'Brumley et al. (2019) PNAS' (defaults to 0, i.e. no noise).

Default parameters:

  * `motility`
  * `turn_rate_forward = 2.3` Hz
  * `turn_rate_backward = 1.9` Hz
  * `state = 0.0` s
  * `state_m = 0.0` s
  * `state_z = 0.0` s
  * `rotational_diffusivity = 0.26` rad²/s
  * `adaptation_time_m = 1.29` s
  * `adaptation_time_z = 0.28` s
  * `gain_forward = 2.7` 1/s
  * `gain_backward = 1.6` 1/s
  * `binding_affinity = 0.39` μM
  * `chemotactic_precision = 0.0`
  * `radius = 0.5` μm
