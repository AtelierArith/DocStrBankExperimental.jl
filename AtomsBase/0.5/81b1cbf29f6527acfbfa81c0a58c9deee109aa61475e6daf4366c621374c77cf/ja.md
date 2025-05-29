```
isolated_system(atoms::AbstractVector; kwargs...)
```

渡された `atoms` を無限の真空に配置することで [`FlexibleSystem`](@ref) を構築します（分子系のモデリングのための標準的なセットアップ）。追加の `kwargs` はカスタムシステムプロパティとして保存されます。

# 例

水素分子を構築する

```julia-repl
julia> hydrogen = isolated_system([:H => [0, 0, 1.]u"bohr", :H => [0, 0, 3.]u"bohr"])
```
