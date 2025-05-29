制約 H=0, G>=0 に関連する切断二次モジュールで f を分解します：

```
WS0, WS, P, v, M = sos_decompose(f, G, H, X, d, optimizer; exact = false, round = Inf64 )
```

このようにして 

$$
f = \sum_k \omega_{0,k} q_{0,k}^2 + \sum_j (\sum_k \omega_{j,k} q_{j,k}^2)*G[j] + \sum_i P[i]*H[i]              (+)
$$

ここで

  * f は分解する多項式です
  * G = [...] は非負制約です
  * H = [...] は等式制約です
  * X は変数の集合です
  * d は緩和の次数です
  * `optimizer` (オプション) は SDP プログラムを解くために使用される最適化器です。デフォルト値は `MMT[:optimizer]` です
  * `exact = true` の場合、正確な分解が有理係数で計算されます。
  * オプション `round = p` が提供されると、最大で p 桁の丸めが使用されます。

出力分解において、 

  * WS0 = [w0, Q0] で、w0 は (+) の重み $\omega_{0,k}$ の配列で、Q0 は次数 $\le 2d -\deg(G[i])$ の多項式 (q_{0,k} in (+)) の配列です
  * WS = [WS1, WS2, ...] で、WSi は (+) の重み $\omega_{j,k}$ と多項式 $q_{j,k}$ に対する WS0 です
  * P[i] は次数 $\le 2d - \deg(H[i])$ の多項式です
  * v は S0 の最大の最小固有値で、$(X^d)^t S0 (X^d) = \sum_k \omega_{0,k} q_{0,k}^2$ が (*) で成り立ちます
  * `M` は JuMP 最適化モデルです
