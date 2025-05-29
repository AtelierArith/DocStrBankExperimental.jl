```
Neumann{F,P} <: AbstractBoundaryCondition{F,P}
```

A Neumann boundary condition with fields `f` and `p` (default `p = nothing`), with `f` being a function of the form `f(u, t, p)` and `p` being the parameters for `f`.

A Neumann boundary condition takes the form

$$
\dfrac{\partial u}{\partial x}(a, t) = f(u(a, t), t, p),
$$

where `a` is one of the endpoints. 

# Constructors

```
Neumann(f::Function, p = nothing) -> Neumann(f, p)
Neumann(; f, p = nothing)         -> Neumann(f, p)
Neumann(v::Number)                -> Neumann((u, t, p) -> oftype(u, v), nothing)
```
