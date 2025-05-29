完全なチェビシェフ多項式の重みを、近似サンプル `y`、チェビシェフ極値で評価されたチェビシェフ多項式 `poly`、および多項式の `order` を使用してマルチスレッドで計算します。重みを含む多次元配列を返します。チェビシェフ重みの要素型は `poly` の要素型によって決まります。

# シグネチャ

w = chebyshev*weights*extrema_threaded(y,poly,order)

# 例

```
julia> nodes1 = nodes(5,:chebyshev_extrema,[9.0,3.0])
julia> nodes2 = nodes(5,:chebyshev_extrema,[1.5,0.5])
julia> poly1 = chebyshev_polynomial(3,nodes1)
julia> poly2 = chebyshev_polynomial(3,nodes2)
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = 3
julia> weights = chebyshev_weights_extrema_threaded(y,(poly1.poly,poly2.poly),ord)
[1.66416      0.598461   -0.02372     0.00280618
  0.263786     0.0948622  -0.00375987  0.0
 -0.024647    -0.0088635   0.0         0.0
  0.00386243   0.0         0.0         0.0]
```
