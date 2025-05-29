```julia
FixedPoint!(SC::SelfCons; tol::Float64=1e-6, max_iter::Int64=100) 
FixedPoint!(SC::SelfCons, fileName::String; tol::Float64=1e-6, max_iter::Int64=100, checkpoint_interval::Int64 = 10) 
```

Runs a fixed point iteration on the `SelfCons` SC with a convergence tolerance of `tol` per input, and a maximum iteration cutoff of `max_iter`. Optionally can also pass a `fileName` to checkpoint and save the results in. Can pass a kwarg `checkpoint_interval` to set the checkpoint frequency.
