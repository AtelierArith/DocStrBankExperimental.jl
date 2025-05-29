```
obj = heart_phantom(
    circumferential_strain, radial_strain, rotation_angle; 
    heart_rate, asymmetry
)
```

Heart-like LV 2D phantom. The variable `circumferential_strain` and `radial_strain` are for streching (if positive)  or contraction (if negative). `rotation_angle` is for rotation.

# Keywords

  * `circumferential_strain`: (`::Real`, `=-0.3`) contraction parameter. Between -1 and 1
  * `radial_strain`: (`::Real`, `=-0.3`) contraction parameter. Between -1 and 1
  * `rotation_angle`: (`::Real`, `=15.0`, `[º]`) maximum rotation angle
  * `heart_rate`: (`::Real`, `=60`, `[bpm]`) heartbeat frequency
  * `temporal_asymmetry`: (`::Real`, `=0.2`) time fraction of the period in which the systole occurs. Therefore, diastole lasts for `period * (1 - temporal_asymmetry)`

# Returns

  * `obj`: (`::Phantom`) Heart-like LV phantom struct
