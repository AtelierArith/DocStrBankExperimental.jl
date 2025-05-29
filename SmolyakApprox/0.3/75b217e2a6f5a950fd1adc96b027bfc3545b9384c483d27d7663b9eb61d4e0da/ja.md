チェビシェフ多項式を基底関数として使用し、近似サンプル `y` と `逆補間行列` を用いてスモリャク多項式近似の重みを計算します。スモリャク多項式の重みを含むベクトルを返します。

# シグネチャ

w = smolyak*weights(y,grid,inverse*interpolation_matrix)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> iim = smolyak_inverse_interpolation_matrix(g,mi)
julia> w = smolyak_weights(y,iim)
```
