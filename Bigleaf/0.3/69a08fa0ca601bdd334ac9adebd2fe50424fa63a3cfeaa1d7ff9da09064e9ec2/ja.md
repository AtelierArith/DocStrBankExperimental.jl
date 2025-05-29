```
setinvalid_afterprecip!(df; min_precip = 0.01, hours_after = 24.0)
```

降水後のレコードを `:valid` 列で偽に設定します。

# 引数

  * df: `:datetime` と `:precip` 列を持つデータフレームで、`：datetime` に従って昇順にソートされています。

オプション:

  * `min_precip` (タイムステップあたりのmm): 効果的な降水と見なされるための最小降水量。
  * `hours_after`: 降水イベント後に無効と見なされる時間

# 値

修正された `:valid` 列を持つ `df`。
