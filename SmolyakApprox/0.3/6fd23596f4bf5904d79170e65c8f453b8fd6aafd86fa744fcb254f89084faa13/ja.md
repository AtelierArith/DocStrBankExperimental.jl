Smolyak近似計画を構築します。`node_type`関数、次元数`d`、近似層`mu`、および近似`domain`（デフォルトは[1.0,-1.0]^d）を指定します。SApproxPlan構造体を返します。

# シグネチャ

splan = smolyal*plan(node*type,d,mu,domain)

# 例

```
julia> splan = smolyak_plan(chebyshev_extrema,2,2)
julia> splan = smolyak_plan(clenshaw_curtis_equidistant,2,[2,2])
julia> splan = smolyak_plan(chebyshev_extrema,2,2,[3.0 1.5; 2.0 0.5])
julia> splan = smolyak_plan(clenshaw_curtis_equidistant,2,[2,2],[3.0 1.5; 2.0 0.5])
```
