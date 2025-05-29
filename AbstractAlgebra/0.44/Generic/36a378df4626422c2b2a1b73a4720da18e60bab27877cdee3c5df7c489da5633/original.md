```
is_submodule(M::AbstractAlgebra.FPModule{T}, N::AbstractAlgebra.FPModule{T}) where T <: RingElement
```

Return `true` if $N$ was constructed as a submodule of $M$. The relation is taken transitively (i.e. subsubmodules are submodules for the purposes of this relation, etc). The module $M$ is also considered a submodule of itself for this relation.
