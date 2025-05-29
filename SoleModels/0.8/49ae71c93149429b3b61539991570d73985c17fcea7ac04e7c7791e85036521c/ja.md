```
struct ConstantModel{O} <: LeafModel{O}
    outcome::O
    info::NamedTuple
end
```

最も単純なモデルのタイプは `ConstantModel` です。これは常に同じ結果を出力する `LeafModel` です。

# 例

```julia-repl
julia> SoleModels.LeafModel(2) isa SoleModels.ConstantModel

julia> SoleModels.LeafModel(sum) isa SoleModels.FunctionModel
┌ Warning: 効率に関する懸念から、Juliaの関数をFunctionWrapper{O,Tuple{SoleModels.AbstractInterpretation}}構造体にラップすることを検討してください。ここでOはその戻り値の型です。
└ @ SoleModels ~/.julia/dev/SoleModels/src/base.jl:337
true

```

詳細は [`apply`](@ref), [`FunctionModel`](@ref), [`LeafModel`](@ref) を参照してください。
