```
@eqrelation Name a/b = c
@eqrelation Name a*b = c
```

次の既存の同値型 `Name <: Equivalence` に次元 `a` と `b` の間に比例または反比例の関係を追加します。次元 `a` と `b` は `Unitful.Energy` のような量の型エイリアスとして指定する必要があります。

# 例

```@julia
using Unitful: Energy, Mass, c0
struct MassEnergy <: Equivalence end
@eqrelation MassEnergy Energy/Mass = c0^2
```

粒子の静止系において、そのエネルギーは質量に比例します。上記のように `MassEnergy` 同値を定義することで、`uconvert(massunit, energy, MassEnergy())` および `uconvert(energyunit, massunit, MassEnergy())` を介してエネルギーと質量の間の変換が可能になります。
