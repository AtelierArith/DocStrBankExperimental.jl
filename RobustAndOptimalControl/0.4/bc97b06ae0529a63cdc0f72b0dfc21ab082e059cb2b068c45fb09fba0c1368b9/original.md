```
frequency_separation(sys, ω)
```

Decomponse `sys` into `sys = sys_slow + sys_fast`, where `sys_slow` contain all modes with eigenvalues with absolute value less than `ω` and `sys_fast` contain all modes with eigenvalues with absolute value greater than or equal to `ω`.
