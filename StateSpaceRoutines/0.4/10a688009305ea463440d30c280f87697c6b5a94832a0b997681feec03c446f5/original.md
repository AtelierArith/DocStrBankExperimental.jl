```
mutation!(Φ, Ψ, QQ, det_HH, inv_HH, φ_new, y_t, s_t, s_t1, ϵ_t, c, n_mh_steps;
    poolmodel = false)
```

Mutate particles by taking Metropolis-Hastings steps in the `ϵ_t` space. This function modifies `s_t` and `ϵ_t` in place and returns `accept_rate`.
