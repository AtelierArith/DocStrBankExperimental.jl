```
LinearOperator(A, B⁻¹, temp)
```

A helper object used to apply the action of a linear operator, whose matrix representation is given by `A`, in the basis whose metric inverse is `B⁻¹`. For orthogonal bases (such as e.g. [`FiniteDifferences`](@ref) and [`FEDVR`](@ref)), only multiplication by `A` is necessary, but non-orthonal bases (such as [`BSpline`](@ref)) necessitates the application of the metric inverse as well.
