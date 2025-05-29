```
compose(G::LieGroup{𝔽,AdditionGroupOperation}, g, h)
compose!(G::LieGroup{𝔽,AdditionGroupOperation}, k, g, h)
```

`g`と`h`の群演算の合成を、`G`上の[`AdditionGroupOperation`](@ref)に関して計算します。これは、`g+h`を呼び出すことにフォールバックし、`+`はそれに応じてオーバーロードされていると仮定されます。

これは`k`のインプレースで計算できます。
