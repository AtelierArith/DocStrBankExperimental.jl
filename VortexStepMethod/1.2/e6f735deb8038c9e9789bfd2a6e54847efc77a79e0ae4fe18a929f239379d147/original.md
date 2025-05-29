```
linearize(solver::Solver, body_aero::BodyAerodynamics, wing::RamAirWing, y::Vector{T}; 
    theta_idxs=1:4, delta_idxs=nothing, va_idxs=nothing, omega_idxs=nothing, kwargs...) where T
```

Compute the Jacobian matrix for a ram air wing around an operating point using finite differences.

# Arguments

  * `solver`: VSM solver instance (must be initialized)
  * `body_aero`: Aerodynamic body representation
  * `wing`: RamAirWing model to linearize
  * `y`: Input vector at operating point, containing a combination of control angles and velocities

# Keyword Arguments

  * `theta_idxs`: Indices of twist angles in input vector (default: 1:4)
  * `delta_idxs`: Indices of trailing edge deflection angles (default: nothing)
  * `va_idxs`: Indices of velocity components `[vx, vy, vz]` (default: nothing)
  * `omega_idxs`: Indices of angular velocity components `[ωx, ωy, ωz]` (default: nothing)
  * `kwargs...`: Additional arguments passed to the `solve!` function

# Returns

  * `jac`: Jacobian matrix (∂outputs/∂inputs)
  * `results`: Output vector at the operating point [Fx, Fy, Fz, Mx, My, Mz, group_moments...]

# Example

```julia
# Initialize wing and solver
wing = RamAirWing("path/to/body.obj", "path/to/foil.dat")
body_aero = BodyAerodynamics([wing])
solver = Solver(body_aero)

# Define operating point with 4 control angles, velocity, and angular rates
y_op = [zeros(4);        # 4 twist control angles (rad)
       [15.0, 0.0, 0.0]; # Velocity vector (m/s)
       zeros(3)]         # Angular velocity (rad/s)

# Compute Jacobian
jac, results = linearize(
    solver, body_aero, wing, y_op;
    theta_idxs=1:4,      # Twist angles
    va_idxs=5:7,         # Velocity components
    omega_idxs=8:10      # Angular rates
)
```
