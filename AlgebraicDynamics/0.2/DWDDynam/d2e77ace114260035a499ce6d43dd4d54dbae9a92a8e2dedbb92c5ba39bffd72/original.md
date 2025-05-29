```
eval_dynamics(m::AbstractMachine, u::AbstractVector, x:AbstractVector{F}, p, t) where {F<:Function}
eval_dynamics(m::AbstractMachine{T}, u::AbstractVector, x:AbstractVector{T}, p, t) where T
```

Evaluates the dynamics of the machine `m` at state `u`, parameters `p` and time `t`. The exogenous variables are set by `x`, which may be a collection either of functions $x_i(t)$ or of constant values. In either case, the length of `x` must equal the number of inputs to `m`.
