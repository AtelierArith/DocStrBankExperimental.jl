```
meanrecurrencetime(R[; lmin=2, theiler])
```

再帰行列 `R` の平均再帰時間を計算します。デフォルトで `lmin` より短い行（デフォルトは2）と、すべての点を Theiler ウィンドウ内で除外します（キーワード引数 `theiler` のデフォルト値と使用法については [`rqa`](@ref) を参照してください）。

[`rt_average`](@ref) と同等です。
