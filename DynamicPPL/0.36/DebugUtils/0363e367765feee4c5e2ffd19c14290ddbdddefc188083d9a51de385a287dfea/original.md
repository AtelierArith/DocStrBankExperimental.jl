```
check_model([rng, ]model::Model; kwargs...)
```

Check that `model` is valid, warning about any potential issues.

See [`check_model_and_trace`](@ref) for more details on supported keyword arguments and details of which types of checks are performed.

# Returns

  * `issuccess::Bool`: Whether the model check succeeded.
