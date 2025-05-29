```
next_φ(φ_old, coeff_terms, log_e_1_terms, log_e_2_terms, n_obs, r_star, stage;
    fixed_sched = [], findroot = bisection, xtol = 1e-3)
```

次の温度調整因子 `φ_new` を返します。もし `isempty(fixed_sched)` であれば、InEff(φ*new) = r*star を設定することで適応的に `φ_new` を選択します。そうでなければ、`fixed_sched[stage]` を返します。
