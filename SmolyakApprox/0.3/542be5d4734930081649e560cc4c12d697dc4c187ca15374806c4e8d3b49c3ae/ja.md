マルチスレッドを使用して、近似サンプル `y`、近似 `grid`、`multi_index`、および近似 `domain`（デフォルトは [-1.0,1.0]^d）を使用して、分割線形基底関数を用いた Smolyak 多項式近似の重みを計算します。Smolyak 多項式の重みを含むベクトルを返します。

# シグネチャ

w = smolyak*pl*weights*threaded(y,grid,multi*index,domain)

# 例

```
julia> g,mi = smolyak_grid(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> w = smolyak_pl_weights_threaded(y,g,mi,[1.0 1.0; 0.0 0.0])
```
