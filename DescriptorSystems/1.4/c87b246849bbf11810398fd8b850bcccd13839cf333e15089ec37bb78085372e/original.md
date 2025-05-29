```
sys = horzcat(sys1,sys2)
sys = [sys1 sys2]
sys = horzcat(systems...)
```

Concatenate horizontally two systems `sys1` and `sys2` or several descriptor systems `systems...`  by concatenating the input vectors of individual systems. This corresponds to the horizontal  concatenation of their transfer function matrices.  Concatenation of systems with constant matrices, vectors, or scalars having the same row dimensions  or with UniformScalings is also supported.  
