```
convert_pidparams_from_to(kp, ki, kd, from::Symbol, to::Symbol)
```

Convert PID parameters from `from` form to `to` form.

The `from` and `to` forms can be chosen as one of the following

  * `:standard` - $K_p(1 + 1/(T_i s) + T_d s)$
  * `:series` - $K_c(1 + 1/(τ_i s))(τ_d s + 1)$
  * `:parallel` - $K_p + K_i/s + K_d s$
