```
set_output_bounds!(mpc;ymin,ymax,
                ks, soft, binary,prio)
```

Adds the constraints lb ≤ C x  ≤ ub for the time steps k ∈ ks 

  * `soft` marks if the constraint should be softened (default false)
  * `binary` marks if either the upper or lower bounds should be enforced with equality (default false)
  * `prio` marks the relative priority of the constraint (default 0)
