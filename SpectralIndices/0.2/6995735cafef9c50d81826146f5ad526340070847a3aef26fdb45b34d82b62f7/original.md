```
compute_kernel(kernel, params=nothing; kwargs...)
```

Compute a specified kernel using either provided parameters or keyword arguments.

# Arguments

  * `kernel`: The kernel function to use. Should be one of `linear`, `poly`, or `RBF`.
  * `params`: (Optional) A `Dict`, `DataFrame`, or `YAXArray` containing parameters for the kernel computation.
  * `kwargs...`: Keyword arguments that will be converted to parameters if `params` is not provided.

# Returns

  * The result of the kernel computation, the type of which depends on the input type.

# Examples

```julia
result = compute_kernel(linear; params=Dict("a" => 1, "b" => 2))
```
