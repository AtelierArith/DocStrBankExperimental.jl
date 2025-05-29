```
apply_local!(
    local_matrix::AbstractMatrix, local_vector::AbstractVector,
    global_dofs::AbstractVector, ch::ConstraintHandler;
    apply_zero::Bool = false
)
```

[`apply!`](@ref)と似ていますが、`local_matrix`と`local_vector`内で制約された自由度の縮約を行います。これは、グローバルシステムに組み込まれる前に行われます。

キーワード引数`apply_zero`が`true`の場合、すべての不均一性は`0`に設定されます（cf. [`apply!`](@ref) vs [`apply_zero!`](@ref)）。

このメソッドは、すべての制約が「ローカル」である場合にのみ使用できます。つまり、制約が要素の自由度（`global_dofs`）の外にある自由度と結合していない場合です。このような制約の縮約には、グローバル行列/ベクトルのエントリに書き込む必要があるためです。そのような場合には、代わりに[`apply_assemble!`](@ref)を使用できます。

このメソッドは破壊的であることに注意してください。定義上、`local_matrix`と`local_vector`を変更します。
