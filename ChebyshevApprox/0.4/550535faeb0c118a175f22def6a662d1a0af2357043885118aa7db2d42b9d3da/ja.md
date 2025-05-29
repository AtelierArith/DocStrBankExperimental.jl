`order`で指定されたチェビシェフ多項式の2階導関数を、`nodes`構造体で指定された各点で計算します。`nodes.points`の要素は[1.0,-1.0]の範囲内でなければなりません。ChebPoly型を返します。多項式の要素型は`x`の要素型によって決まります。

# シグネチャ

P = chebyshev*polynomial*sec_deriv(order,x)

# 例

```
julia> n = nodes(2,:chebyshev_nodes)
ChebRoots{Float64, Float64}([-0.7071067811865476, 0.7071067811865476], [1.0, -1.0])

julia> P = chebyshev_polynomial_sec_deriv(3,n)
ChebPoly{Float64}([0.0 0.0 4.0 -16.970562748477143; 0.0 0.0 4.0 16.97056274847714], ChebRoots{Float64, Float64})
```
