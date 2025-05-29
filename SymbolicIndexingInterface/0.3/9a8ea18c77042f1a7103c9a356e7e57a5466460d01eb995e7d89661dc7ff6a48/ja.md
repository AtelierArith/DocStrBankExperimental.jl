```
setp_oop(indp, sym)
```

値プロバイダー `valp` と値 `val` を受け取り、`sym` に設定されたパラメータで `parameter_values(valp)` を返す関数を返します。これにより、格納されている値の型を変更でき、[`remake_buffer`](@ref) を活用します。`sym` はインデックス、シンボリック変数、または前述の配列/タプルである可能性があります。

値プロバイダーが `parameter_values` と `remake_buffer` を実装している必要があります。
