```
struct ConstantModel{O} <: LeafModel{O}
    outcome::O
    info::NamedTuple
end
```

最も単純なモデルのタイプは `ConstantModel` です。これは常に同じ結果を出力する [`LeafModel`](@ref) です。

# 例

```julia-repl
julia> cm = ConstantModel(2);
julia> outcome(cm)
2
```

他にも [`apply`](@ref) や [`LeafModel`](@ref) を参照してください。
