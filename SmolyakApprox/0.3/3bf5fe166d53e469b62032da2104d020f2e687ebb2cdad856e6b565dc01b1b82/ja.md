すべての次元で関数 `f` を数値的に積分するために、Clenshaw-Curtis 法を使用し、`pos` を除いて Smolyak 多項式で関数を近似します。関数を返します。

# シグネチャ

integral = smolyak*clenshaw*curtis(f,plan,pos)

# 例

```
julia> f(x) = sum(x.^2)
julia> splan = smolyak_plan(chebyshev_extrema,4,8,[ones(1,4); zeros(1,4)])
julia> integral = smolyak_clenshaw_curtis(f,splan,4)
julia> integral(0.5)
1.2499999999999996
```
