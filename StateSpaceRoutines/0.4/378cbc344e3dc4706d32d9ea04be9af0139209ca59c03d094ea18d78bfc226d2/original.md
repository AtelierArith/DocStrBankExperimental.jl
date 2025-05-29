```
selection!(norm_weights, s_t1_temp, s_t_nontemp, ϵ_t;
    resampling_method = :multinomial)
```

Resample particles using `norm_weights`. This function modifies `s_t1_temp`, `s_t_nontemp`, and `ϵ_t` in place.
