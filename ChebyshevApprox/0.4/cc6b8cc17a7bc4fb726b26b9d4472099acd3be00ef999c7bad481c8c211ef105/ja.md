マルチスレッドを使用して、近似サンプル `y` と近似 `plan` が与えられたときに `x` で評価されたチェビシェフ多項式のヘッセ行列を評価する関数を作成します。

# シグネチャ

h = chebyshev*hessian*threaded(y,plan)

# 例

```
julia> nodes1 = nodes(5,:chebyshev_nodes,[9.0,3.0])
julia> nodes2 = nodes(5,:chebyshev_nodes,[1.5,0.5])
julia> g = Grid((nodes1,nodes2))
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> plan = CApproxPlan(g,ord,dom)
julia> h = chebyshev_hessian_threaded(y,plan)
julia> h([5.5,0.9])
[-0.0118667   0.0661025
  0.0661025  -0.42678]
```
