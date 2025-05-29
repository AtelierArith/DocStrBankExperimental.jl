`refltype(W::ComplexReflectionGroup` or coset`)` または `reflection_type(W)`

は、`W` を分類する `Vector{TypeIrred}` を返します（[`TypeIrred`](@ref)を参照）。`refltype` は、REPL で `W` を表示するために使用されます。`refltype` の結果または `TypeIrred` に対する `indices` 関数は、可約成分の各標準生成子の `gens(W)` におけるインデックスを示します。`W` の REPL 表示では、これらのインデックスは期待されるものである場合は省略されます（成分は期待されるインデックスで順序付けられています）。

```julia-repl
julia> W=coxgroup(:D,3) # D₃ は無秩序の A₃
A₃₍₁₃₂₎

julia> t=refltype(W)
A₃₍₁₃₂₎

julia> indices(t)
3-element Vector{Int64}:
 1
 3
 2
```
