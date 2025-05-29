Smolyak多項式を評価します。これは、`weights`、評価する点`point`、近似`grid`、多重インデックス`multi_index`、および近似`domain`（デフォルトは[1.0,-1.0]^d）を使用して、部分線形基底関数を形成します。スカラーを返します。

# シグネチャ

yhat = smolyak*pl,evaluate(weights,point,grid,multi*index,domain)

# 例

```
julia> g,mi = smolyak_grid(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_pl_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> yhat = smolyak_pl_evaluate(w,[0.37,0.71],g,mi,[1.0 1.0; 0.0 0.0])
0.5549321821467206
```
