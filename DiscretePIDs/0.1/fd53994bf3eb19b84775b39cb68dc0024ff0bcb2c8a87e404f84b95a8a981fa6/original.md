```
K, Ti, Td = parallel2standard(Kp, Ki, Kd)
```

Convert parameters from form "parallel" form $K_p + K_i/s + K_d s$

to "standard" form used in DiscretePID: $K(1 + 1/(T_i s) + T_d s)$

You may provide either three arguments or an array with three elements in the same order.
