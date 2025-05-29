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

ビリニア形式を記述するためのコンストラクタであり、a(u,v) = ((β ⋅ ∇) u,v) であり、ユーザーが指定したデータ関数 β を使用します。ユーザーはまた、対流が適用されるコンポーネントの数 (ncomponents) を指定する必要があります。u と v のオペレーターは変更可能です（これが合理的な結果につながる場合）。
