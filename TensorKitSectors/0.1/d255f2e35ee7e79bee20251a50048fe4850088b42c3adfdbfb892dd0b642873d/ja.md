```
const FermionSpin = SU2Irrep ⊠ FermionParity
FermionSpin(j::Real)
```

フェルミオンスピンは、$SU₂$ 表現 `j` とフェルミオンパリティの直積として表され、`2 * j` が奇数の場合、フェルミオンパリティは奇数であるという制約があります。

参照: [`SU2Irrep`](@ref), [`FermionParity`](@ref)
