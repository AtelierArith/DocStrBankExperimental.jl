```
SciMLOperators.cached_operator(L::AbstractQuantumObject, u)
```

Allocate caches for [`AbstractQuantumObject`](@ref) `L` for in-place evaluation with `u`-like input vectors.

Here, `u` can be in either the following types:

  * `AbstractVector`
  * [`Ket`](@ref)-type [`QuantumObject`](@ref) (if `L` is an [`Operator`](@ref))
  * [`OperatorKet`](@ref)-type [`QuantumObject`](@ref) (if `L` is a [`SuperOperator`](@ref))
