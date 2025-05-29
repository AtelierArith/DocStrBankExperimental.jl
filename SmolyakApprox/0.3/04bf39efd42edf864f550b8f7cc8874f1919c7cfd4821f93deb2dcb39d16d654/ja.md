数値的に関数 `f` をすべての次元で積分し、近似 `plan` に従ってスモリャク多項式で関数を近似します。`method` として :clenshaw*curtis または gauss*Chebyshev_quad を使用します。スカラーを返します。

# シグネチャ

integral = smolyak_integrate(f,plan,method)

# 例

```
julia> f(x) = sum(x.^2)
julia> splan = smolyak_plan(chebyshev_extrema,4,8,[ones(1,4); zeros(1,4)])
julia> integral = smolyak_integrate(f,splan,:clenshaw_curtis)
1.3333333333333328
julia> integral = smolyak_integrate(f,splan,:gauss_chebyshev_quad)
1.3318637929187602
```
