```
K, Ti, Td, N = parallel2standard(Kp, Ki, Kd, Tf)
```

Convert parameters from form "parallel" form with first-order filter $K_p (br-y) + K_i (r-y)/s - K_d s y/(Tf s + 1)$

to "standard" form used in DiscretePID: $K (br-y + (r-y)/(T_i s) - T_d s y/(T_d / N s + 1))$

You may provide either four arguments or an array with four elements in the same order.
