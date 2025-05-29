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

ビリニア形式を記述するためのコンストラクタで、a(u,v) = ((β ⋅ ∇) u,v) であり、ユーザーが指定したデータ関数 β を使用します。ユーザーは、対流が適用されるコンポーネントの数 (ncomponents) も指定する必要があります。u と v のオペレーターは、（それが合理的な結果につながる場合）変更できます。
