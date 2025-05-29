Smolyak多項式の部分導関数を計算します。これは、Chebyshev基底関数を使用して形成され、`weights`、多項式を評価する`point`、`multi_index`、近似`domain`、および微分する変数のインデックス`pos`が与えられます。スカラーを返します。

# シグネチャ

deriv = smolyak*derivative(weights,point,multi*index,domain,pos)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> deriv1 = smolyak_derivative(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0],1)
0.40368169538532706
julia> deriv2 = smolyak_derivative(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0],2)
0.5250627466157657
```
