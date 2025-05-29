```
lorentzian(f, u)
```

ローレンツ関数の値を計算します。

# 引数

  * `f::AbstractVector`: 周波数値
  * `u::Vector`: パラメータ [振幅, ニー周波数]

# 戻り値

  * ローレンツ値のベクトル: amp/(1 + (f/knee)²)
