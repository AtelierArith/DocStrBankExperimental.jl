```
LinearCurve(proportional_term::Float64)
LinearCurve(proportional_term::Float64, constant_term::Float64)
```

線形の入力-出力曲線で、一定の限界レートを表します。ゼロの無負荷コスト（すなわち、一定の平均レート）を持つ場合もあれば、持たない場合もあります。

# 引数

  * `proportional_term::Float64`: 限界レート
  * `constant_term::Float64`: オプション、ゼロ生産時のコスト、デフォルトは `0.0`
