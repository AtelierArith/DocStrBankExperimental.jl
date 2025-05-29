```julia
PlanarEntryFunction(; name, kwargs...)

```

`ODEFunction`を返します。Planar Entry dynamicsのためのものです。結果は`Memoize.jl`でキャッシュされます。

状態の順序は次の通りです: `[γ, v, r, θ]`。

パラメータの順序は次の通りです: `[R, P, H, m, A, C, μ]`。

# 拡張ヘルプ

### 使用法

`name`キーワード引数は`PlanarEntry`に渡されます。他のすべてのキーワード引数は直接`SciMLBase.ODEFunction`に渡されます。

```julia
f = PlanarEntryFunction()
let u = randn(4), p = randn(7), t = NaN # 時間不変
    f(u, p, t)
end
```
