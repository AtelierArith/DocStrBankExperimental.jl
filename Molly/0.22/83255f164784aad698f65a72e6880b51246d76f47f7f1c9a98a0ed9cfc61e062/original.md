```
apply_position_constraints!(sys, coord_storage; n_threads::Integer=Threads.nthreads())
apply_position_constraints!(sys, coord_storage, vel_storage, dt;
                            n_threads::Integer=Threads.nthreads())
```

Applies the system constraints to the coordinates.

If `vel_storage` and `dt` are provided then velocity corrections are applied as well.
