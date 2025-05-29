Smolyak多項式を評価します。これは、与えられた`weights`、多項式を評価する`point`、`multi_index`、および近似`domain`（デフォルトは[1.0,-1.0]^d）を使用して形成されるChebyshev基底関数を使用します。スカラーを返します。

# シグネチャ

yhat = smolyak*evaluate(weights,point,multi*index,domain)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> yhat = smolyak_evaluate(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
0.5953026581237828
```
