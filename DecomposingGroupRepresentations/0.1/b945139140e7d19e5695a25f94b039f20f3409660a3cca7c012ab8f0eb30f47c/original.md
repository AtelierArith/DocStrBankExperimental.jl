```
algebra(::AbstractGroup{Lie, F}) -> AbstractLieAlgebra{F}
```

Returns the Lie algebra of a given Lie group.

# Examples

```julia-repl
julia> SO3 = LieGroup("SO", 3);

julia> algebra(SO3)
LieAlgebra 𝖘𝖔(3)
 number type (or field): ComplexF64
 weight type: Int64
 dimension: 3
 rank (dimension of Cartan subalgebra): 1
```
