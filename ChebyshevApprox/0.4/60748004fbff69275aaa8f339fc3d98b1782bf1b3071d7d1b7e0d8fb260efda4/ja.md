チェビシェフ多項式における重みを、近似サンプル `y` と近似プラン `plan` に基づいて計算します。指定された `plan` に含まれる重みを含む多次元配列を返します。チェビシェフ重みの要素型は、近似 `plan` に指定された近似点の要素型によって決まります。

# シグネチャ

w = chebyshev_weights(y,plan)

# 例

```
julia> nodes1 = nodes(5,:chebyshev_nodes,[9.0,3.0])
julia> nodes2 = nodes(5,:chebyshev_nodes,[1.5,0.5])
julia> g = Grid((nodes1,nodes2))
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> plan = CApproxPlan(g,ord,dom)
julia> weights = chebyshev_weights(y,plan)
[1.66416      0.598458    -0.0237052     0.00272941
  0.26378      0.0948592   -0.00375743    0.000432628
 -0.0246176   -0.00885287   0.000350667  -4.03756e-5
  0.00372291   0.00133882  -5.30312e-5    6.10598e-6]

julia> nodes1 = nodes(9,:chebyshev_nodes,[9.0,3.0])
julia> nodes2 = nodes(9,:chebyshev_nodes,[1.5,0.5])
julia> poly1 = chebyshev_polynomial(3,nodes1)
julia> poly2 = chebyshev_polynomial(3,nodes2)
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:9, j in 1:9]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> plan = CApproxPlanPoly((poly1,poly2),ord,dom)
julia> weights = chebyshev_weights(y,plan)
[1.66416      0.598458    -0.0237052     0.00272941
  0.26378      0.0948592   -0.00375743    0.000432628
 -0.0246176   -0.00885287   0.000350667  -4.03756e-5
  0.00372291   0.00133882  -5.30312e-5    6.10598e-6]
```
