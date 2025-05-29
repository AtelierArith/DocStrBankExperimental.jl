`order`で指定された次数のチェビシェフ多項式を、`nodes`構造体で指定された各点で計算します。`nodes.points`の要素は[1.0,-1.0]の範囲内でなければなりません。ChebPoly型を返します。多項式の要素型は`x`の要素型によって決まります。

# シグネチャ

P = chebyshev_polynomial(order,x)

# 例

```
julia> n = nodes(2,:chebyshev_nodes)
ChebRoots{Float64, Float64}([-0.7071067811865476, 0.7071067811865476], [1.0, -1.0])

julia> P = chebyshev_polynomial(3,n)
ChebPoly{Float64}([1.0 -0.7071067811865476 2.220446049250313e-16 0.7071067811865472; 1.0 0.7071067811865475 -2.220446049250313e-16 -0.7071067811865478], ChebRoots{Float64, Float64})
```
