```julia
set_ε_grad_Inf_norm!(conf::LevenbergMarquardt_Conf,
                     ε_grad_Inf_norm::Float64)
```

停止基準を修正する $|\nabla f|_\infty\le\epsilon$

参照: [`LevenbergMarquardt_Conf`](@ref) 
