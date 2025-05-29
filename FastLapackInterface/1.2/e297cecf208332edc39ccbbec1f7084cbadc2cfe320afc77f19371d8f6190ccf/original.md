```
resize!(ws, A; kwargs...)
```

Resizes the `ws` to be appropriate for use with matrix `A`. The `kwargs` can be used to communicate which features should be supported by the [`Workspace`](@ref), such as left and right eigenvectors while using [`EigenWs`](@ref). This function is mainly used for automatic resizing inside [`LAPACK functions`](@ref LAPACK).
