```
    ConstrainedODEFunction(r1,r2,B1,B2[,L][,C])
```

This specifies the functions and operators that comprise an ODE problem with the form

$\dfrac{dy}{dt} = Ly - B_1 z + r_1(y,t)$

$B_2 y + C z = r_2(x,t)$

where $y$ is the state, $z$ is a constraint force, and $x$ is an auxiliary state describing the constraints.

The optional linear operator `L` defaults to zeros. The `B1` and `B2` functions must be of the respective in-place forms `B1(dy,z,x,p)` (to compute the action of `B1` on `z`) and `B2(dz,y,x,p)` (to compute the action of `B2` on `y`). The function `r1` must of the in-place form `r1(dy,y,x,p,t)`, and `r2` must be in the in-place form `r2(dz,x,p,t)`. The `C` function can be omitted, but if it is included, then it must be of the form `C(dz,z,x,p)` (to compute the action of `C` on `z`). Alternatively, one can supply out-of-place forms, respectively, as `B1(z,x,p)`, `B2(y,x,p)`, `C(z,x,p)`, `r1(y,x,p,t)` and `r2(x,p,t)`.

An optional keyword argument `param_update_func` can be used to set a function that updates problem parameters with the current solution. This function must take the in-place form `f(q,u,p,t)` or out of place form `f(u,p,t)` to create some `q` based on `u`, where `y = state(u)`, `z = constraint(u)` and `x = aux_state(u)`. (Note that `q` might enter the function simply as `p`, to be mutated.) This function can be used to update `B1`, `B2`, and `C`, for example.

We can also include another (unconstrained) set of equations to the set above in order to update `x`:

$\dfrac{dx}{dt} = r_{1x}(u,p,t)$

In this case, the right-hand side has access to the entire `u` vector. We would pass the pair of `r1` functions as an `ArrayPartition`.
