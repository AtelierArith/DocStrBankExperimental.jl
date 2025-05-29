```
compose(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, h)
compose!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, k, g, h)
```

群の演算の合成を、[`AbstractMultiplicationGroupOperation`](@ref) に関して、[`LieGroup`](@ref) `G` 上の `g` と `h` で計算します。これは、`g*h` を呼び出すことにフォールバックし、`*` はそれに応じてオーバーロードされていると仮定されます。

これは `k` のインプレースで計算できます。
