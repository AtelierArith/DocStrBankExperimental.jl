```
add_constraint!(mpc::MPC;
    Ax, Au, Ar, Aw, Ad, Aup,
    ub, lb, ks, soft, binary, prio)
add_constraint!(mpc;Ax,Au,ub,lb,
                ks, soft, binary,prio)
```

Adds the constraints lb ≤ Ax xₖ + Au uₖ ≤ ub for the time steps k ∈ ks (additional terms Ar rₖ, Aw wₖ, Ad dₖ, Aup u⁻ₖ are possible)

  * `soft` marks if the constraint should be softened (default false)
  * `binary` marks if either the upper or lower bounds should be enforced with equality (default false)
  * `prio` marks the relative priority of the constraint (default 0)
