```
Neumann
```

Instance of a [`ConditionType`](@ref) used for declaring that an edge  has a `Neumann` condition. `Neumann` conditions  take the form 

$$
\vb q(x, y, t) \vdot \vu n_\sigma = a(x, y, t, u)
$$

where $\vb q$ is the flux function and $\vu n_\sigma$ is the  outward unit normal vector field on the associated edge (meaning, for example,  the normal vector to an edge `pq` would point to the right of `pq`).

When providing a `Neumann` condition, the function you provide  takes the form

```
a(x, y, t, u, p)
```

where `(x, y)` is the point, `t` is the current time, and `u` is the  solution at the point `(x, y)` at time `t`, as above, with an extra  argument `p` for additional parameters. 
