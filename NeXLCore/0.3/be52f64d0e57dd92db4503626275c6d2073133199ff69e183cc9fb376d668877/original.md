trajectory(eval::Function, p::T, reg::Region, scf::Function=transport; minE::Float64=50.0) where {T <: Particle} trajectory(eval::Function, p::T, reg::Region, scf::Function, terminate::Function) where { T <: Particle }

Run a single particle trajectory from `p` to `minE` or until the particle exits `reg`.

  * `eval(part::T, region::Region)` a function evaluated at each scattering point
  * `p` defines the initial position, direction and energy of the particle (often created with `gun(T, ...)`)
  * `reg` The outer-most region for the trajectory (usually created with `chamber()`)
  * `scf` A function from (<:Particle, Material) -> ( λ, θ, ϕ, ΔE ) that implements the transport dynamics
  * `minE` Stopping criterion
  * `terminate` a function taking `T` and `Region` that returns false except on the last step (like `terminate = (pc,r)->pc.energy < 50.0`)
