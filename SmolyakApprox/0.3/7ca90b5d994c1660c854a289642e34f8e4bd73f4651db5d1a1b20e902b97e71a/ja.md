Smolyak多項式を評価し、`weights`とSmolyak多項式を使用してスカラーを返します。

# シグネチャ

yhat = smolyak_evaluate(weights,polynomial)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> p = smolyak_polynomial([0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
julia> yhat = smolyak_evaluate(w,p)
0.5953026581237828
```
