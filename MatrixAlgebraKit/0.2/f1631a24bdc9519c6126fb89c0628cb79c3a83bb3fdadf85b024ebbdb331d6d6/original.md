```
MatrixAlgebraKit.select_algorithm(f, A, alg::AbstractAlgorithm)
MatrixAlgebraKit.select_algorithm(f, A, alg::Symbol; kwargs...)
MatrixAlgebraKit.select_algorithm(f, A, alg::Type; kwargs...)
MatrixAlgebraKit.select_algorithm(f, A; kwargs...)
MatrixAlgebraKit.select_algorithm(f, A, (; kwargs...))
```

Decide on an algorithm to use for implementing the function `f` on inputs of type `A`.

If `alg` is an `AbstractAlgorithm` instance, it will be returned as-is.

If `alg` is a `Symbol` or a `Type` of algorithm, the return value is obtained by calling the corresponding algorithm constructor; keyword arguments in `kwargs` are passed along  to this constructor.

If `alg` is not specified (or `nothing`), an algorithm will be selected  automatically with [`MatrixAlgebraKit.default_algorithm`](@ref) and  the keyword arguments in `kwargs` will be passed to the algorithm constructor. Finally, the same behavior is obtained when the keyword arguments are passed as the third positional argument in the form of a `NamedTuple`. 
