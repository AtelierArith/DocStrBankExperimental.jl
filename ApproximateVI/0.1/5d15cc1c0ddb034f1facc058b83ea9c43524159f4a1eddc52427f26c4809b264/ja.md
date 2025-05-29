```
合成二次元問題
```

# 例

```julia-repl
julia> logp = exampleproblem1() # 近似する対象分布
julia> q, logev = VI(logp, randn(2), S = 100, iterations = 10_000, show_every = 50)
julia> using Plots # 独立してインストールする必要があります。
julia> x = -3:0.02:3
julia> contour(x, x, map(x -> exp(logp(collect(x))), Iterators.product(x, x))', fill=true, c=:blues, colorbar = false) # 対象をプロット
julia> contour!(x, x, map(x -> pdf(q,(collect(x))), Iterators.product(x, x))', color="red", alpha=0.3) # 近似qをプロット
```
