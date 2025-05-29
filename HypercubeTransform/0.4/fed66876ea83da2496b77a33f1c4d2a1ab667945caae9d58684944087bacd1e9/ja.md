```
NamedDist(d::NamedTuple{N})
NamedDist(;dists...)
```

名前付きの分布 `N`。これは、名前が付けられた一連の確率変数を構築するのに便利です。

```julia-repl
julia> d = NamedDist((a=Normal(), b = Uniform(), c = MvNormal(randn(2), rand(2))))
julia> x = rand(d)
(a = 0.13789342, b = 0.2347895, c = [2.023984392, -3.09023840923])
julia> logpdf(d, x)
```

NamedDist に渡される NamedDist 値は、分布の抽象コレクションでもあることに注意してください。

```julia-repl
julia> d = NamedDist(a = Normal(),
                     b = MvNormal(ones(2)),
                     c = (Uniform(), InverseGamma())
                     d = (a = Normal(), Beta)
                    )
```

これが内部でどのように行われるかは、実装の詳細と見なされており、公開インターフェースの一部ではありません。
