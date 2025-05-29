```
algebra(::AbstractGroup{Lie, F}) -> AbstractLieAlgebra{F}
```

与えられたリー群のリー代数を返します。

# 例

```julia-repl
julia> SO3 = LieGroup("SO", 3);

julia> algebra(SO3)
LieAlgebra 𝖘𝖔(3)
 number type (or field): ComplexF64
 weight type: Int64
 dimension: 3
 rank (dimension of Cartan subalgebra): 1
```
