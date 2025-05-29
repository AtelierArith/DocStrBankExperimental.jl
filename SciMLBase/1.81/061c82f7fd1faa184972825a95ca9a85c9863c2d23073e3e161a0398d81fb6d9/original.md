AffineDiffEqOperator{T} <: AbstractDiffEqOperator{T}

`Ex: (A₁(t) + ... + Aₙ(t))*u + B₁(t) + ... + Bₘ(t)`

AffineDiffEqOperator{T}(As,Bs,du_cache=nothing)

Takes in two tuples for split Affine DiffEqs

1. update_coefficients! works by updating the coefficients of the component operators.
2. Function calls L(u, p, t) and L(du, u, p, t) are fallbacks interpreted in this form. This will allow them to work directly in the nonlinear ODE solvers without modification.
3. f(du, u, p, t) is only allowed if a du_cache is given
4. B(t) can be Union{Number,AbstractArray}, in which case they are constants. Otherwise they are interpreted they are functions v=B(t) and B(v,t)

Solvers will see this operator from integrator.f and can interpret it by checking the internals of As and Bs. For example, it can check isconstant(As[1]) etc.
