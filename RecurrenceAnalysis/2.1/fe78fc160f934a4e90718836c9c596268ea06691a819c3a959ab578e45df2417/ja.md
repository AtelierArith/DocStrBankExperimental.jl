```
rt_max(R[; lmin=2, theiler])
```

再帰行列 `R` に含まれる最長の再帰時間を計算し、`lmin`（デフォルトは2）より短い行と、全ての点を Theiler ウィンドウ内から除外します（デフォルト値とキーワード引数 `theiler` の使用については [`rqa`](@ref) を参照してください）。
