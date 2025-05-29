```
assign_migration!(network::Network, migration_data::Dict, species::Type{<:Species})
```

ユーザーが指定した遷移率で`migration`フィールドが populatedされた`Network`インスタンスを返します。

# ユーザーへの注意:

  * 入力データはネストされた辞書としてフォーマットする必要があります。最初のレベルは関連するライフステージと遺伝子を示し、2番目のレベルにはノードのto/fromと遷移率が含まれます。
  * 入力データで指定されていないステージと遺伝子の組み合わせは、デフォルトの遷移率がゼロのまま保持されます。
