```
DynamicSystem([TF=eltype(assembly),] assembly; kwargs...)
```

Initialize an object of type [`DynamicSystem`](@ref).

# Arguments:

  * `TF:`(optional) Floating point type, defaults to the floating point type of `assembly`
  * `assembly`: Assembly of rigidly connected nonlinear beam elements

# Keyword Arguments

  * `force_scaling`: Factor used to scale system forces/moments internally.  If  not specified, a suitable default will be chosen based on the entries of the  beam element compliance matrices.
