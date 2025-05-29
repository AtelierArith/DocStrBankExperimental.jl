```
next_φ(φ_old, coeff_terms, log_e_1_terms, log_e_2_terms, n_obs, r_star, stage;
    fixed_sched = [], findroot = bisection, xtol = 1e-3)
```

Return the next tempering factor `φ_new`. If `isempty(fixed_sched)`, adaptively choose `φ_new` by setting InEff(φ*new) = r*star. Otherwise, return `fixed_sched[stage]`.
