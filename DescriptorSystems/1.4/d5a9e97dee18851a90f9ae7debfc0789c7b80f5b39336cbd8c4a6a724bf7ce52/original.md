```
sys = vertcat(sys1,sys2)
sys = [sys1; sys2]
sys = vertcat(systems...)
```

Concatenate vertically two descriptor systems `sys1` and `sys2` or several descriptor systems `systems...`  by concatenating the output vectors of individual systems. This corresponds to the vertical  concatenation of their transfer function matrices.  Concatenation of systems with constant matrices, vectors, or scalars having the same column dimensions  or with UniformScalings is also supported.  
