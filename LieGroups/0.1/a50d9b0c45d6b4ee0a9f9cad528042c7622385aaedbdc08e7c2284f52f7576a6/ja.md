```
exp(G::LieGroup{𝔽,AdditionGroupOperation}, X)
exp!(G::LieGroup{𝔽,AdditionGroupOperation}, g, X)
```

[`LieGroup`](@ref) と [`AdditionGroupOperation`](@ref) を持つリー群の指数を計算します。これは `g` のインプレースで計算できます。

`e` は対応する `+` に関してゼロ要素に過ぎないため、式は $g=0+X=X$ となります。
