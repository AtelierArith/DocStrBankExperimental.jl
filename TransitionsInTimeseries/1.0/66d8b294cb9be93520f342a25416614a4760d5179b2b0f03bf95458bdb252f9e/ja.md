```
SlopeChangeSignificance(; moe_slope, moe_offset, slope_diff = moe_slope, pvalue = 0.05)
```

[`SlopeChangeResults`](@ref) の結果が統計的に有意かどうかをテストします。

2つのテストが行われます：

1. 選択した `pvalue` に対して、2つの線形セグメント `a + b*t, c + d*t` のフィッティングパラメータ `a, b, c, d` の*誤差の範囲*が指定された誤差の範囲よりも小さいかどうかを確認します。
2. 2つの傾き `b, d` の差が `slope_diff` より大きいかどうかをテストします。

上記の2つのブール値 `&` が最終テストです。

誤差の範囲は、信頼区間のサイズの半分、すなわち信頼区間の半径として知られています。
