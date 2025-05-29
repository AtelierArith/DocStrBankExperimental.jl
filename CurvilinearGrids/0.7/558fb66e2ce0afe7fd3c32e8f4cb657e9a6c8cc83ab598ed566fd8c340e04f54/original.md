```
estimate_wall_distance(
```

ρ::Unitful.Density,   U::Unitful.Velocity,   L::Unitful.Length,   μ::Unitful.DynamicViscosity,   y_plus, )

Estimate the wall-thickness needed to capture a turbulent boundary layer based on the input conditions. This returns (reynolds*number, wall*thickness).
