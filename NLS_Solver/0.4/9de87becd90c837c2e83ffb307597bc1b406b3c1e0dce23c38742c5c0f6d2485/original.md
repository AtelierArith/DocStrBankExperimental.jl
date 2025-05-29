```julia
mutable struct LevenbergMarquardt_BC_Conf <: Abstract_Solver_Conf
    ...
end
```

Use this constructor

```julia
LevenbergMarquardt_BC_Conf()
```

to initialize the bound constrained Levenberg-Marquardt solver default configuration parameters.

To solve a problem with this method, you must then call  [`solve(nls::AbstractNLS, θ_init::AbstractVector, bc::BoundConstraints, conf::Abstract_BC_Solver_Conf)`](@ref) 

See: 

  * [`set_max_iteration!(conf::LevenbergMarquardt_BC_Conf,max_iter::Int)`](@ref)
  * [`set_ε_grad_Inf_norm!(conf::LevenbergMarquardt_BC_Conf,ε_grad_Inf_norm::Float64)`](@ref)
  * [`set_ε_step_Inf_norm!(conf::LevenbergMarquardt_BC_Conf,ε_step_Inf_norm::Float64)`](@ref)
