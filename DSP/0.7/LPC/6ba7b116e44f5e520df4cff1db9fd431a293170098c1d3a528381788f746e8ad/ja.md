```
lpc(x::AbstractVector, p::Int, LPCLevinson())
```

LPC（線形予測符号）推定、Levinson法を使用。 この関数は[1]に記載されている数学を実装しています。

[1] - フィルタ設計と予測におけるウィーナー（RMS）誤差基準（N. Levinson、応用数学の研究 25(1946)、261-278、https://doi.org/10.1002/sapm1946251261）
