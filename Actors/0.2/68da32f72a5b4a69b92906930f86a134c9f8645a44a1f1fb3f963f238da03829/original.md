```
restore(cp::Link; key::Symbol)
```

Tell a checkpointing actor to restore the last taken checkpoint.

# Arguments

  * `cp::Link`:  [`Link`](@ref) to the checkpointing actor,
  * `key::Symbol`: checkpoint key,
  * `level::Int=1`: checkpoint level to restore from.
