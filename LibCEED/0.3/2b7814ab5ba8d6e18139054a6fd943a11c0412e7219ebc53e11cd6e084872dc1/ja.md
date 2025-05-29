```
create_identity_qfunction(c::Ceed, size, inmode::EvalMode, outmode::EvalMode)
```

アイデンティティ [`QFunction`](@ref) を作成します。入力は指定された順序で出力に書き込まれます。これは、[`ElemRestriction`](@ref) と [`Basis`](@ref) の作用のみで表現できる [`Operators`](@ref Operator) に便利です。例えば、p-multigrid の制限および延長オペレーターなどです。バックエンドは、この Q 関数を使用して `CeedOperators` を最適化し、入力データを出力フィールドにコピーすることなく、両方のメモリ位置を同じにすることができます。
