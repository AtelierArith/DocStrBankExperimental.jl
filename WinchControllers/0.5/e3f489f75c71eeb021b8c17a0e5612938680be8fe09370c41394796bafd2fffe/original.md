```
mutable struct CalcVSetIn
```

Component for calculation `v_set_in`, using soft switching.

## Fields

  * wcs::[WCSettings](@ref)
  * mixer2::[Mixer_2CH](@ref): mixer component. Default: `Mixer_2CH(wcs.dt, wcs.t_blend)`
  * input_a: Default: 0
  * input_b: Default: 0
