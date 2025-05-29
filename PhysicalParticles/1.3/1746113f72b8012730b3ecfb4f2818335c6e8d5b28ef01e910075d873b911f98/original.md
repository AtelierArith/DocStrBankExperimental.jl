```
rotate(data, vec::PVector, θ::Number, center::PVector; vel::Bool = true)
```

Rotate all particles in data around direction vector `vec` at `center` point by angle `θ`.

  * `vel::Bool = false`: Rotate velocity around origin at the same time.
