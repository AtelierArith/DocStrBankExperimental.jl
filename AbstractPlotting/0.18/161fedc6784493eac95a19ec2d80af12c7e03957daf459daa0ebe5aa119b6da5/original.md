```
rotate_cam!(scene::Scene, theta_v::Number...)
rotate_cam!(scene::Scene, theta_v::VecTypes)
```

Rotate the camera of the Scene by the given rotation. Passing `theta_v = (α, β, γ)` will rotate the camera according to the Euler angles (α, β, γ).
