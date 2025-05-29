```julia
mutable struct LevenbergMarquardt_Conf <: Abstract_Solver_Conf
    ...
end
```

Use this constructor

```julia
LevenbergMarquardt_Conf()
```

to initialize the Levenberg-Marquardt solver default configuration parameters.

To solve a problem with this method, you must then call  [`solve(nls::AbstractNLS, θ_init::AbstractVector, conf::Abstract_Solver_Conf)`](@ref) 

See: 

  * [`set_max_iteration!(conf::LevenbergMarquardt_Conf,max_iter::Int)`](@ref)
  * [`set_ε_grad_Inf_norm!(conf::LevenbergMarquardt_Conf,ε_grad_Inf_norm::Float64)`](@ref)
  * [`set_ε_step_Inf_norm!(conf::LevenbergMarquardt_Conf,ε_step_Inf_norm::Float64)`](@ref)
