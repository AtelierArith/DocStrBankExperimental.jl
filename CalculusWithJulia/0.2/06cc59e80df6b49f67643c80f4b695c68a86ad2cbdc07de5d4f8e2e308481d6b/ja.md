```
riemann(f, a, b, n; method="right"
```

関数 `f` の定積分を `[a,b]` の等サイズの分割を用いて `n+1` のサイズで近似計算します。

method: `"right"` (デフォルト), `"left"`, `"trapezoid"`, `"simpsons"`, `"ct"`, `"m̃"` (区間の最小値), `"M̃"` (区間の最大値)

例:

```
f(x) = exp(x^2)
riemann(f, 0, 1, 1000)   # デフォルトの右リーマン和
riemann(f, 0, 1, 1000; method="left")       # 左の和
riemann(f, 0, 1, 1000; method="trapezoid")  # 台形法を使用
riemann(f, 0, 1, 1000; method="simpsons")   # シンプソンの法則を使用
```
