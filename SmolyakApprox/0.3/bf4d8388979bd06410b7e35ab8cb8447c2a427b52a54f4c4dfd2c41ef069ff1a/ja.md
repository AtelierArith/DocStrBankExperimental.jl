関数 `f` をすべての次元で数値的に積分するために、Clenshaw-Curtis 法を使用し、近似 `plan` に従って Smolyak 多項式で関数を近似します。スカラーを返します。

# シグネチャ

integral = smolyak*clenshaw*curtis(f,plan)

# 例

```
julia> f(x) = sum(x.^2)
julia> splan = smolyak_plan(chebyshev_extrema,4,8,[ones(1,4); zeros(1,4)])
julia> integral = smolyak_clenshaw_curtis(f,splan)
1.3333333333333328
```
