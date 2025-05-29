チェビシェフ多項式を基底関数として使用し、近似サンプル `y` と `逆補間行列` を与えて、双曲線交差多項式近似における重みを計算します。双曲線交差多項式の重みを含むベクトルを返します。

# シグネチャ

w = hyperbolic*cross*weights(y,inverse*interpolation*matrix)

# 例

```
julia> g,mi = hyperbolic_cross_grid(chebyshev_extrema,2,3,5,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> iim = hyperbolic_cross_inverse_interpolation_matrix(g,mi)
julia> w = hyperbolic_cross_weights(y,iim)
```
