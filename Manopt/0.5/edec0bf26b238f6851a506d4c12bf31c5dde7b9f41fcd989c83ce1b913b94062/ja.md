```
DebugCost <: DebugAction
```

現在のコスト関数の値を表示します。 [`get_cost`](@ref)を参照してください。

# コンストラクタ

```
DebugCost()
```

# パラメータ

  * `format="$prefix %f"`: 出力を印刷するためのフォーマット
  * `io=stdout`: デバッグを印刷するためのデフォルトストリーム。
  * `long=false`: フォーマットを `f(x):`（デフォルト）または `current cost:` とコストに設定するための短い形式
