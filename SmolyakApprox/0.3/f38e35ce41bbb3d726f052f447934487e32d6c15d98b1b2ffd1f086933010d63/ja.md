チェビシェフ多項式を基底関数として使用し、近似サンプル `y`、近似 `grid`、`multi_index`、および近似 `domain`（デフォルトは [1.0,-1.0]^d）を用いて、マルチスレッドでスモリャク多項式近似の重みを計算します。スモリャク多項式の重みを含むベクトルを返します。

# シグネチャ

w = smolyak*weights*threaded(y,grid,multi_index,domain)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> w = smolyak_weights_threaded(y,g,mi,[1.0 1.0; 0.0 0.0])
```
