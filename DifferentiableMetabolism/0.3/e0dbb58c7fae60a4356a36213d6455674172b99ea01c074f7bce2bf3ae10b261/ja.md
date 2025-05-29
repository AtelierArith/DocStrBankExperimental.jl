```julia
optimized_values(
    model::ConstraintTrees.ConstraintTree,
    parameters::Dict{Symbol, Float64};
    optimizer,
    settings,
    objective,
    sense
)

```

`optimizer`を使用して`model`を解決し、`parameters`を代入します。オプションの引数はCOBREXAと同じです。

モデルが正常に解決しない場合は`nothing`を返します。そうでない場合は、解決ツリーの名前付きタプルと、プライマル変数の値、デュアル変数の値を含むベクトルを返します。

これらのデュアルは、それぞれ[`equality_constraints`](@ref)および[`inequality_constraints`](@ref)を呼び出したときの制約出力に従って順序付けられています。
