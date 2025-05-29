```
inv(G::LieGroup{𝔽,AdditionGroupOperation}, g)
inv!(G::LieGroup{𝔽,AdditionGroupOperation}, h, g)
```

群の逆元 $g^{-1}$ を計算します。これは [`AdditionGroupOperation`](@ref) の場合、$-g$ に簡略化されます。これは `h` のインプレースで行うことができます。
