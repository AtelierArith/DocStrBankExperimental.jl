```
syst = similarity_transform(sys, T; unitary=false)
```

`sys`に対して類似変換 `T : Tx̃ = x` を実行します。

```
Ã = T⁻¹AT
B̃ = T⁻¹ B
C̃ = CT
D̃ = D
```

`unitary=true` の場合、`T` はユニタリ行列と見なされ、逆行列の代わりに行列の随伴が使用されます。詳細は [`balance_statespace`](@ref) を参照してください。
