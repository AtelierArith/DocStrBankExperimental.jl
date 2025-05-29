```
make_set_initial_cache(model::AbstractModel)
```

Returns the set*initial*cache! function, which updates the auxiliary state `p` in place with the initial values corresponding to Y(t=t0) = Y0.

In principle, this function is not needed, because in the very first evaluation of either `explicit_tendency` or `implicit_tendency`, at t=t0, the auxiliary state is updated using the initial conditions for Y=Y0. However, without setting the initial `p` state prior to running the simulation, the value of `p` in the saved output at t=t0 will be unset.

Furthermore, specific methods of this function may be useful for models which store time indepedent spatially varying parameter fields in the auxiliary state. In this case, `update_aux!` does not need to do anything, but they do need to be set with the initial (constant) values before the simulation can be carried out.
