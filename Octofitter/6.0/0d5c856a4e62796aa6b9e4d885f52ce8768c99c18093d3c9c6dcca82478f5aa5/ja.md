```
UniformCircular(domain=2π)
```

連続的で周期的なドメインにパラメータ化された変数を作成します。2つの正規分布に従う乱数変数 :Ωx と :Ωy を作成し、`atan(:Ωy, :Ωx)` に従って導出変数を使用して円形ドメインにマッピングします。サンプラーが自由にラップできるため、例えば `Ω = Uniform(-pi, pi)` を使用するよりも効率的である可能性があります。

例:

```julia
Variables(;
    a = Uniform(1, 10),
    e = Uniform(0, 1),
    UniformCircular(:Ω)...,
)
```
