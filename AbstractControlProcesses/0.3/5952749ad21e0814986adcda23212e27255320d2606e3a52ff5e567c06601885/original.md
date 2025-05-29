```
b = bias(P::AbstractProcess)
```

Return an input bias for the process. This could be, i.e., the constant input u₀ around which a nonlinear system is linearized, or whatever other bias might exist on the input. `length(b) = num_inputs(P)`
