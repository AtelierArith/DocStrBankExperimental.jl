```
CanOrbital{T, D, NN} <: AbstractSpinOrbital{T, D}
```

ハートリー–フォック状態のフォック行列を対角化する一連のものである標準スピン軌道の空間部分（軌道）とその占有情報。これは、軌道に対応するモードの最大占有数（すなわち標準軌道）が2であることを意味します。`CanOrbital`の構築については[`genCanOrbitals`](@ref)を参照してください。

≡≡≡ フィールド ≡≡≡

`energy::T`: 軌道に対応する固有エネルギー。

`index::Int`: 同じスピン構成内の軌道のインデックス。

`nuc::NTuple{NN, String}`: 研究対象の系の原子核。

`nucCoords::NTuple{NN, NTuple{D, T}}`: 対応する原子核の座標。

`occu::NTuple{2, Array{Bool, 0}}`: 2つのスピン構成の占有。

`orbital::GTBasisFuncs{T, D, 1}`: 空間軌道部分。
