```
sys = append(systems...)
```

Append the descriptor systems `systems` by concatenating the input and output vectors of individual systems. This corresponds to the block diagonal concatenation of  their transfer function matrices.  Appending systems with constant matrices, vectors or scalars or with UniformScalings is also supported. 
