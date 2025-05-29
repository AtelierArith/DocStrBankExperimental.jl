```
MCUSUM(k, p, value = 0.0, St = zeros(p))
```

多変量累積和 (MCUSUM) 統計量。

### 引数

  * `k::Float64`: 許容パラメータの値。
  * `p::Int`: 監視する変数の数。
  * `value::Float64`: 統計量の初期値。デフォルトは 0.0。
  * `St::Vector{Float64}`: 現在の時刻 `t` における多変量累積和を表すベクトル。

### 例

```
stat = MCUSUM(0.25, 2, 0.0, [0.0, 0.0])
```

### 参考文献

Crosier, R. B. (1988). Multivariate Generalizations of Cumulative Sum Quality-Control Schemes. Technometrics, 30(3), 291-303. https://doi.org/10.2307/1270083
