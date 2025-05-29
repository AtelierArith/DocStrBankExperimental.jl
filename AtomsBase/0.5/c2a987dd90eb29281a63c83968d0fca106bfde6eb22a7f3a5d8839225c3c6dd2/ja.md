```
atomic_system(atoms::AbstractVector, cell_vectors, periodicity; kwargs...)
```

渡された `atoms` と境界ボックスおよび条件を使用して [`FlexibleSystem`](@ref) を構築します。追加の `kwargs` はカスタムシステムプロパティとして保存されます。

# 例

最初の2次元のみが周期的なボックス内に水素分子を構築します。

```julia-repl
julia> cell_vectors = [[10.0, 0.0, 0.0], [0.0, 10.0, 0.0], [0.0, 0.0, 10.0]]u"Å"
julia> pbcs = (true, true, false)
julia> hydrogen = atomic_system([:H => [0, 0, 1.]u"bohr",
                                 :H => [0, 0, 3.]u"bohr"],
                                  cell_vectors, pbcs)
```
