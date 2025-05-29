```
sys = parallel(sys1, sys2) 
sys = sys1 + sys2
```

Connect the descriptor systems `sys1` and `sys2` in parallel such that `sys = sys1 + sys2`.  This coupling corresponds to the addition of their transfer function matrices.  Parallel coupling of systems with constant matrices or vectors having the same row and column dimensions  or with UniformScalings is also supported.  Parallel coupling with a constant is equivalent to elementwise parallel coupling of  the transfer function matrix with the constant. 
