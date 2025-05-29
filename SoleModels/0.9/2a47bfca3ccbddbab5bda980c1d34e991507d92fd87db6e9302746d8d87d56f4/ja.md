```
abstract type LeafModel{O} <: AbstractModel{O} end
```

葉モデルのための抽象型、つまり、結果が他のモデルに依存しないモデルであり、計算の最下部を表します。

一般に、[`AbstractModel`](@ref) は他の `AbstractModel` をラップすることができます。この場合、結果はインスタンスオブジェクトに適用される内部モデルに依存する可能性があります。そうでなければ、モデルは *葉* または *最終* と見なされ、`AbstractModel` の木の *葉* となります。

# 例

```julia-repl
julia> SoleModels.LeafModel(2) isa SoleModels.ConstantModel

julia> SoleModels.LeafModel(sum) isa SoleModels.FunctionModel
┌ Warning: Over efficiency concerns, please consider wrappingJulia Function's into FunctionWrapper{O,Tuple{SoleModels.AbstractInterpretation}} structures,where O is their return type.
└ @ SoleModels ~/.julia/dev/SoleModels/src/base.jl:337
true
```

他に [`AbstractModel`](@ref)、[`ConstantModel`](@ref)、[`FunctionModel`](@ref) を参照してください。
