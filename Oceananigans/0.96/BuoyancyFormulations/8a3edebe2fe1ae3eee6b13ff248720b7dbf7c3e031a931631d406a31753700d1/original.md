```
SeawaterBuoyancy{FT, EOS, T, S} <: AbstractBuoyancyFormulation{EOS}
```

Buoyancy formulation for seawater. `T` and `S` are either `nothing` if both temperature and salinity are active, or of type `FT` if temperature or salinity are constant, respectively.
