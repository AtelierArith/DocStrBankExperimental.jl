```
rotate(data::Array, vec::PVector, θ::Number; vel::Bool = true)
```

Rotate all particles in data around direction vector `vec` by angle `θ`.

  * `vel::Bool = false`: Rotate velocity around origin at the same time.
