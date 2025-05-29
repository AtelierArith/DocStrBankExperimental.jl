```
add_interface_entries!(
    sp::SparsityPattern, dh::DofHandler, ch::Union{ConstraintHandler, Nothing};
    topology::ExclusiveTopology, keep_constrained::Bool = true,
    interface_coupling::AbstractMatrix{Bool},
)
```

セル間のインターフェース上のDoF結合に対応するスパースパターン`sp`にエントリを追加します。これはDofHandler `dh`によって説明されます。

# キーワード引数

  * `topology`: グリッドに対応するトポロジー。
  * `keep_constrained`: 制約されたDoFのエントリを保持するかどうか（`keep_constrained = true`）またはスパースパターンから削除するか（`keep_constrained = false`）。`keep_constrained = false`はConstraintHandler `ch`を渡す必要があります。
  * `interface_coupling`: インターフェースを横断するフィールド/コンポーネント間の結合。
