```
control(P::AbstractProcess, u)
```

Send a control signal to the process. `u` must have dimension equal to `num_inputs(P)`
