```
Robin{F,P} <: AbstractBoundaryCondition{F,P}
```

A Robin boundary condition with fields `f` and `p` (default `p = nothing`), with `f` being a function of the form `f(u, t, p)` that returns a `Tuple` `(a₂, b₂)`  and `p` being the parameters for `f`.

A Robin boundary condition takes the form

$$
dL/dt = a₂(u, t, p) + b₂(u, t, p)∂u/∂x,
$$

where `f(u, t, p) = (a₂(u, t, p), b₂(u, t, p))`. 

# Constructors

```
Robin(f::Function, p = nothing) -> Robin(f, p)
Robin(; f, p = nothing)         -> Robin(f, p)
Robin(a::Number, b::Number)     -> Robin((u, t, p) -> (oftype(u, a), oftype(u, b)))
Robin(a₂::Function, b₂::Function, p = nothing) -> Robin((u, t, p) -> (a₂(u, t, p), b₂(u, t, p)), p)
```
