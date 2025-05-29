テンソル積チェビシェフ多項式の重みをマルチスレッドを使用して計算します。与えられた近似サンプル `y`、チェビシェフ拡張点 `nodes`、多項式の `order`、および `domain` に基づいています。重みを含む多次元配列を返します。チェビシェフ重みの要素型は `nodes` の要素型によって決まります。

# シグネチャ

w = chebyshev*weights*extended_threaded(y,nodes,order,domain)

# 例

```
julia> nodes1 = chebyshev_extended(5,[9.0,3.0])
julia> nodes2 = chebyshev_extended(5,[1.5,0.5])
julia> y = [nodes1[i]^0.3*nodes2[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> weights = chebyshev_weights_extended_threaded(y,(nodes1,nodes2),ord,dom)
[1.66393      0.598444    -0.0238922     0.00277041
  0.263837     0.0948909   -0.00378841    0.000439284
 -0.0249247   -0.00896435   0.000357891  -4.14991e-5
  0.00379791   0.00136595  -5.45338e-5    6.32345e-6]
```
