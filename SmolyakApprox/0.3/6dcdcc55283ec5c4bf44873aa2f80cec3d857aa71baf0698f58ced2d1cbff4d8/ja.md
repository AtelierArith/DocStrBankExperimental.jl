チェビシェフ多項式を基底関数として使用し、近似サンプル `y`、近似 `grid`、`multi_index`、および近似 `domain`（デフォルトは [1.0,-1.0]^d）を考慮して、Smolyak多項式近似における重みを計算します。Smolyak多項式の重みを含むベクトルを返します。

# シグネチャ

w = smolyak*weights(y,grid,multi*index,domain)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> w = smolyak_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
```
