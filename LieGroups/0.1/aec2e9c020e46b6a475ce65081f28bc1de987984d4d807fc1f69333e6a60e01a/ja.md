```
identity_element(G::LieGroup{𝔽,AbelianMultiplicationGroupOperation})
identity_element!(G::LieGroup{𝔽,AbelianMultiplicationGroupOperation}, e)
```

[`Identity`](@ref)の点表現を返します。これは[`AbelianMultiplicationGroupOperation`](@ref)の場合、1要素です。

`e`が`mutable`であれば、これを`e`で計算できます。
