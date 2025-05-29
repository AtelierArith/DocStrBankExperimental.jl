```julia
set_ε_grad_Inf_norm!(conf::LevenbergMarquardt_Conf,
                     ε_grad_Inf_norm::Float64)
```

Modify the stopping criterion $|\nabla f|_\infty\le\epsilon$

See: [`LevenbergMarquardt_Conf`](@ref) 
