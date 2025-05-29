```
abstract NEP
```

`NEP`オブジェクトは非線形固有値問題を表します。すべてのNEPは以下を実装する必要があります。

```julia
size(nep::NEP,d)
```

そして、少なくとも次のうちの1つを実装する必要があります。

  * M = [`compute_Mder(nep::NEP,λ::Number,i::Integer=0)`](@ref)
  * V = [`compute_Mlincomb(nep::NEP,λ::Number,V::AbstractVecOrMat,a::Vector)`](@ref) (または`compute_Mlincomb!`)
  * MM = [`compute_MM(nep::NEP,S,V)`](@ref)
