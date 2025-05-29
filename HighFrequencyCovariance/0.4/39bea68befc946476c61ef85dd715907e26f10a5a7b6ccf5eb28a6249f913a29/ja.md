```
get_returns(dd::DataFrame; rescale_for_duration::Bool = false)
```

価格の長形式の `DataFrame` をリターンの `DataFrame` に変換します。

### 入力

  * `dd` - :Time という列を持ち、他のすべての列が各期間の資産価格である `DataFrame`。
  * `rescale_for_duration` - リターンを共通の時間間隔を反映するように再スケールするべきか。

### 返り値

  * リターンの `DataFrame`。
