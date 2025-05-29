```
inv(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g)
inv!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, h, g)
```

群の逆元 $g^{-1}$ を計算します。これは [`AbstractMultiplicationGroupOperation`](@ref) に対しては、乗法逆元 $g^{-1}$ に簡略化されます。これは `h` のインプレースで行うことができます。
