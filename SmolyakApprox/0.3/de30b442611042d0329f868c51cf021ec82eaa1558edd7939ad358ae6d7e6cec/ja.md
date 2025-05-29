Smolyak多項式のヘッセ行列を計算します。これは、Chebyshev基底関数を使用して形成され、`weights`、多項式を評価する`point`、`multi_index`、および近似`domain`が与えられます。行列を返します。

# シグネチャ

hess = smolyak*hessian(weights,point,multi*index,domain)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> hess = smolyak_hessian(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
[ -2.53475  1.06753
   1.06753  0.199234]
```
