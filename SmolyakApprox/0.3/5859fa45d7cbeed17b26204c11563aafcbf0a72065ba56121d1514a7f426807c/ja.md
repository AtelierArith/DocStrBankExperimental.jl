`node`を近似グリッドで、`multi-index`と近似`domain`（デフォルトは[-1.0,1.0]^d）を指定してSmolyak多項式を計算します。多項式の基底関数を`node`で評価したベクトルを返します。

# シグネチャ

spoly = smolyak*polynomial(node,multi*index,domain)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> node = g[5,:]
julia> sploy = smolyak_polynomial(node,mi,[1.0 1.0; 0.0 0.0])
```
