```
lyap_taylorinteg(f!, q0, t0, tmax, order, abstol[, jacobianfunc!=nothing];
    maxsteps::Int=500, parse_eqs::Bool=true)
lyap_taylorinteg(f!, q0, trange, order, abstol[, jacobianfunc!=nothing];
    maxsteps::Int=500, parse_eqs::Bool=true)
```

Similar to [`taylorinteg`](@ref) for the calculation of the Lyapunov spectrum. Note that the number of `TaylorN` variables should be set previously by the user (e.g., by means of `TaylorSeries.set_variables`) and should be equal to the length of the vector of initial conditions `q0`. Otherwise, whenever `length(q0) != TaylorSeries.get_numvars()`, then `lyap_taylorinteg` throws an `AssertionError`. Optionally, the user may provide a Jacobian function `jacobianfunc!` to evaluate the current value of the Jacobian. Otherwise, the current value of the Jacobian is computed via automatic differentiation using `TaylorSeries.jl`.
