```
apply_assemble!(
    assembler::AbstractAssembler, ch::ConstraintHandler,
    global_dofs::AbstractVector{Int},
    local_matrix::AbstractMatrix, local_vector::AbstractVector;
    apply_zero::Bool = false
)
```

`local_matrix` と `local_vector` を `assembler` のグローバルシステムに組み込むために、まず [`apply_local!`](@ref) を使用して制約の凝縮を行います。

これは、非ローカル制約を処理できるという利点があるため、[`apply_local!`](@ref) の後に [`assemble!`](@ref) を使用するのと似ています。このメソッドは、`global_dofs` のインデックスの外にあるグローバル行列とベクトルのエントリに書き込むことができます。

キーワード引数 `apply_zero` が `true` の場合、すべての不均一性は `0` に設定されます（cf. [`apply!`](@ref) vs [`apply_zero!`](@ref)）。

このメソッドは、`local_matrix` と `local_vector` を変更するため、破壊的であることに注意してください。
