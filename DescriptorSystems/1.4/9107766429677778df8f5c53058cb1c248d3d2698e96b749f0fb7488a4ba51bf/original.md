```
 sys = series(sys1, sys2) 
 sys = sys2*sys1
```

Connect the descriptor systems `sys1` and `sys2` in series such that `sys = sys2*sys1`. This coupling corresponds to the multiplication of their transfer function matrices.  Series coupling of systems with constant matrices and vectors having suitable dimensions  or with UniformScalings is also supported.  Series coupling with a constant is equivalent to elementwise multiplication of  the transfer function matrix with the constant. 
