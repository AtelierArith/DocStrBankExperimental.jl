Struct that holds various precomputed arrays for the semi-implicit correction to prevent gravity waves from amplifying in the shallow water model. The implicit time step between i-1 and i+1 is controlled by the parameter `α` in the range [0, 1]

```
α = 0   means the gravity wave terms are evaluated at i-1 (forward)
α = 0.5 evaluates at i+1 and i-1 (centered implicit)
α = 1   evaluates at i+1 (backward implicit)
α ∈ [0.5, 1] are also possible which controls the strength of the gravity wave dampening.
α = 0.5 slows gravity waves and prevents them from amplifying
α > 0.5 will dampen the gravity waves within days to a few timesteps (α=1)
```

Fields are

  * `α::Any`: [OPTION] coefficient for semi-implicit computations to filter gravity waves, 0.5 <= α <= 1
  * `gravity::Base.RefValue`: Gravity [m/s²], taken from model.planet at initialize!
  * `layer_thickness::Base.RefValue`: Layer thickness [m], taken from model.atmosphere at initialize!
  * `time_step::Base.RefValue`: Time step [s], = αdt = 2αΔt (for leapfrog)
