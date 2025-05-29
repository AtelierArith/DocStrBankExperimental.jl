```
const FermionNumber = U1Irrep ⊠ FermionParity
FermionNumber(a::Int)
```

フェルミオン数を、$U₁$ 表現 `a` とフェルミオンパリティの直積として表します。このとき、フェルミオンパリティは `a` が奇数である場合に限り奇数です。

関連情報: [`U1Irrep`](@ref), [`FermionParity`](@ref)
