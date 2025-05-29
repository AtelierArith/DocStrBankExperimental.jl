```
log(G::LieGroup{𝔽,AdditionGroupOperation}, g)
log!(G::LieGroup{𝔽,AdditionGroupOperation}, X, g)
```

[`LieGroup`](@ref) と [`AdditionGroupOperation`](@ref) を持つ Lie 群の対数を計算します。これは `X` のインプレースで計算できます。

`e` は対応する `+` に関してゼロ要素に過ぎないため、式は $X=g-0=g$ となります。
