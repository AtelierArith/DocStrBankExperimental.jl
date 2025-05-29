```
setsym_oop(indp, sym)
```

値プロバイダー `valp` と値 `val` を受け取り、`state_values(valp), parameter_values(valp)` を返す関数を返します。このとき、`sym` の状態/パラメータは `val` の対応する値に設定されます。これにより、格納される値の型を変更でき、[`remake_buffer`](@ref) を活用します。`sym` はインデックス、記号変数、または前述の配列/タプルである可能性があります。`sym` のすべてのエントリ `s` は `is_variable(indp, s)` または `is_parameter(indp, s)` を満たす必要があります。

値プロバイダーは `state_values`、`parameter_values`、および `remake_buffer` を実装する必要があります。
