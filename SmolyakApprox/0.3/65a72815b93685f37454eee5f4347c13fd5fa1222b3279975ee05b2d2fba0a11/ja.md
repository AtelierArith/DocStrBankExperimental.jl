フルSmolyak多項式の勾配を計算します。これは、`weights`、多項式を評価する`point`、`multi_index`、および近似`domain`を使用して、Chebyshev基底関数を用いて形成されます。1行の行列を返します。

# シグネチャ

grad = smolyak*gradient(weights,point,multi*index,domain)

# 例

```
julia> g,mi = smolyak_grid_full(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_weights_full(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> grad = smolyak_gradient_full(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
[0.403682  0.525063]
```
