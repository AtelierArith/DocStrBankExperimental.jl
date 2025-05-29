```
is_compatible(M::AbstractAlgebra.FPModule{T}, N::AbstractAlgebra.FPModule{T}) where T <: RingElement
```

Return `true, P` if the given modules are compatible, i.e. that they are (transitively) submodules of the same module, P. Otherwise return `false, M`.
