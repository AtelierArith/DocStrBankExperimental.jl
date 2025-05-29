```
solvealgebraicequations(V::AbstractAlgebraicSet, algo::AbstractAlgebraicSolver)::Union{Nothing, Vector{<:Vector}}}
```

代数方程を解きます。`V` は解の集合であり、`algo` はアルゴリズムです。`V` がゼロ次元でない場合は `null` を返し、それ以外の場合は解のリストを返します。
