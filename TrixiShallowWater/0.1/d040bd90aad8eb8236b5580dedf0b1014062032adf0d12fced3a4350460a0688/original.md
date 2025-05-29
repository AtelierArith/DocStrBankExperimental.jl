```
ManningFriction(; n)
```

Creates a Manning friction model for the bottom friction with Manning coefficient `n`. The type is used to dispatch on the respective friction law through the `shear_stress_coefficient` when computing the `shear_stress`.
