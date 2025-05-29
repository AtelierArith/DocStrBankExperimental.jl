```julia
abstract type NormalFlux <: ??
```

有限要素関数の法線フラックスを評価します。

FACES/BFACESでのみ利用可能で、現在はH1およびHdiv要素のみに対応しています。
