完全なチェビシェフ多項式の重みを、近似サンプル `y`、拡張チェビシェフ点で評価されたチェビシェフ多項式 `poly`、および多項式の `order` を使用してマルチスレッドで計算します。重みを含む多次元配列を返します。チェビシェフ重みの要素型は `poly` の要素型によって与えられます。

# シグネチャ

w = chebyshev*weights*extended_threaded(y,poly,order)

# 例

```
julia> nodes1 = nodes(5,:chebyshev_extended,[9.0,3.0])
julia> nodes2 = nodes(5,:chebyshev_extended,[1.5,0.5])
julia> poly1 = chebyshev_polynomial(3,nodes1)
julia> poly2 = chebyshev_polynomial(3,nodes2)
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = 3
julia> weights = chebyshev_weights_extended_threaded(y,(poly1.poly,poly2.poly),ord)
[1.66393      0.598444    -0.0238922   0.00277041
  0.263837     0.0948909   -0.00378841  0.0
 -0.0249247   -0.00896435   0.0         0.0
  0.00379791   0.0          0.0         0.0]
```
