```
Dirichlet{F,P} <: AbstractBoundaryCondition{F,P}
```

A Dirichlet boundary condition with fields `f` and `p` (default `p = nothing`), with `f` being a function of the form `f(u, p)` and `p` being the parameters for `f`. 

A Dirichlet boundary condition takes the form

$$
u(a, t) ↤ f(u(a, t), t, p),
$$

where `a` is one of the endpoints. 

# Constructors

```
Dirichlet(f::Function, p = nothing) -> Dirichlet(f, p)
Dirichlet(; f, p = nothing)         -> Dirichlet(f, p)
Dirichlet(v::Number)                -> Dirichlet((u, t, p) -> oftype(u, v), nothing)
```
