Smolyak多項式近似における重みを計算します。これは、近似サンプル`y`、近似`grid`、`multi_index`、および近似`domain`（デフォルトは[1.0,-1.0]^d）を使用して、部分線形基底関数を用いて形成されます。Smolyak多項式の重みを含むベクトルを返します。

# シグネチャ

w = smolyak*pl*weights(y,grid,multi_index,domain)

# 例

```
julia> g,mi = smolyak_grid(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> w = smolyak_pl_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
```
