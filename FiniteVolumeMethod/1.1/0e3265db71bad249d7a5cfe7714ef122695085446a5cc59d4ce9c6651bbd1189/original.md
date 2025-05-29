```
Dirichlet
```

Instance of a [`ConditionType`](@ref) used for declaring that an edge, or a point, has a `Dirichlet` boundary condition. `Dirichlet` conditions take the form

$$
u(x, y, t) = a(x, y, t, u).
$$

When providing a `Dirichlet` condition, the function you provide takes the form

```
a(x, y, t, u, p)
```

where `(x, y)` is the point, `t` is the current time, and `u` is the solution at the point `(x, y)` at time `t`, as above, with an extra  argument `p` for additional parameters.
