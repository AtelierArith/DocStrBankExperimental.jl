```
rotate(data, yaw::Number, center::PVector; vel::Bool = true)
```

Rotate all particles in data by radian Euler angles (α, β, γ) = (roll, pitch, yaw).

  * `vel::Bool = false`: Rotate velocity around origin at the same time.
