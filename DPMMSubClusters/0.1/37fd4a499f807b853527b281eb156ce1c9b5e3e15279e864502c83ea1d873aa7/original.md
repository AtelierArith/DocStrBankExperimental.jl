```
run_model_from_checkpoint(filename)
```

Run the model from a checkpoint created by it, `filename` is the path to the checkpoint. Only to be run when using the advanced mode, note that the data must be in the same path as previously.

# Example:

```julia
julia> dp = run_model_from_checkpoint("checkpoint__50.jld2")
Loading Model:
  1.073261 seconds (2.27 M allocations: 113.221 MiB, 2.60% gc time)
Including params
Loading data:
  0.000881 seconds (10.02 k allocations: 378.313 KiB)
Creating model:
Node Leaders:
Dict{Any,Any}(2=>Any[2, 3])
Running model:
...
```
