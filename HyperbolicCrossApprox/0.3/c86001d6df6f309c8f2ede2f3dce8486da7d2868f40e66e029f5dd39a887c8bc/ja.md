ハイパーボリッククロス多項式を評価します。これは、`weights`、多項式を評価する`point`、`multi_index`、および近似`domain`（デフォルトは[-1.0,1.0]^d）を使用して形成されます。スカラーを返します。

# シグネチャ

yhat = hyperbolic*cross*evaluate(weights,point,multi*index) yhat = hyperbolic*cross*evaluate(weights,point,multi*index,domain)

# 例

```
julia> g,mi = hyperbolic_cross_grid(chebyshev_extrema,2,3,5,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = hyperbolic_cross_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> yhat = hyperbolic_cross_evaluate(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
0.6100559317314179
```
