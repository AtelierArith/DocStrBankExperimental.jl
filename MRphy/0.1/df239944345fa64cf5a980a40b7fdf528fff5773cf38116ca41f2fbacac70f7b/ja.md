```
mSpinArray(dim::Dims; T1=1.47u"s", T2=0.07u"s", γ=γ¹H, M=[0. 0. 1.])
mSpinArray(mask::BitArray; T1=1.47u"s", T2=0.07u"s", γ=γ¹H, M=[0. 0. 1.])
```

`AbstractSpinArray`をインスタンス化するための例示的な構造体。

# フィールド:

*不変*:

  * `dim::Dims` (nd,): `nM ← prod(dim)`, オブジェクトの次元。
  * `mask::BitArray` (nx,(ny,(nz))): `M`のマスク、`dim == (nx,(ny,(nz)))`

*可変*:

  * `T1::TypeND(T0D, [0,1])` (1,) または (nM,): 縦方向緩和係数。
  * `T2::TypeND(T0D, [0,1])` (1,) または (nM,): 横方向緩和係数。
  * `γ::TypeND(Γ0D, [0,1])`  (1,) または (nM,): ジロ磁気比。
  * `M::TypeND(Real, [2])`   (`count(mask)`, 3):  磁気スピン、(𝑀x,𝑀y,𝑀z)。

# 注意:

オフ共鳴、`Δf`、および位置、`loc`は、スピンに固有ではなく、時間とともに変化する可能性があるため、意図的に含まれていません。これらを含めないことで、例えば動脈スピンラベリングに特化した拡張サブタイプを可能にします。

参照: [`AbstractSpinArray`](@ref)。
