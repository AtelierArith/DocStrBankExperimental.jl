```
add_cell_entries!(
    sp::AbstractSparsityPattern,
    dh::DofHandler,
    ch::Union{ConstraintHandler, Nothing} = nothing;
    keep_constrained::Bool = true,
    coupling::Union{AbstractMatrix{Bool}, Nothing}, = nothing
)
```

セル内のDoF結合に対応するスパースパターン`sp`にエントリを追加します。これはDofHandler `dh`によって説明されます。

# キーワード引数

  * `keep_constrained`: 制約されたDoFのエントリをスパースパターンに保持するかどうか（`keep_constrained = true`）または削除するか（`keep_constrained = false`）。`keep_constrained = false`の場合、ConstraintHandler `ch`を渡す必要があります。
  * `coupling`: 各セル内のフィールド/コンポーネント間の結合。デフォルトでは（`coupling = nothing`）、各セル内のすべてのDoFが互いに結合していると仮定されます。
