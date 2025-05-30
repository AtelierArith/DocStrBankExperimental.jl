```julia
ConvectionOperator(
    β::GradientRobustMultiPhysics.AbstractUserDataType,
    ncomponents::Int64;
    name,
    store,
    AT,
    ansatz_operator,
    test_operator,
    transposed_assembly,
    regions
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

ビリニアフォームのコンストラクタで、a(u,v) = ((β ⋅ ∇) u,v) をユーザー指定のデータ関数 β で記述します。ユーザーは、対流が適用されるコンポーネントの数 (ncomponents) も指定する必要があります。u と v のオペレーターは、合理的な結果につながる場合に変更できます。
