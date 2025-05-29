```
ControlAffineSystem
```

Control affine system described by the dynamics $ẋ = f(x) + g(x)u$ where $x ∈ ℝⁿ$ is the system state, $u ∈ ℝᵐ$ is the control input and $f : ℝⁿ → ℝⁿ$ and $g : ℝⁿ → ℝⁿˣᵐ$ represent the dynamics.

# Fields

  * `name::String` : name of system, e.g., "double integrator", "unicycle", "quadrotor", etc.
  * `n::Int` : state dimension
  * `m::Int` : control dimension
  * `f::Function` : drift dynamics
  * `g::Function` : control directions
