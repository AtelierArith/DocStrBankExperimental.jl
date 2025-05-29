```
calc_bandreps(sgnum::Integer, Dᵛ::Val{D}=Val(3);
              timereversal::Bool=true,
              allpaths::Bool=false,
              explicitly_real::Bool=timereversal)
```

空間群 `sgnum` のバンド表現を次元 `D` で計算し、`BandRepSet` を返します。

## キーワード引数

  * `timereversal` (デフォルト: `true`): バンド表現を誘導するために使用される不変表現が時間反転不変であると仮定するかどうか（すなわち、コア表現であるか、[`realify`](@ref)を参照）。
  * `allpaths` (デフォルト: `false`): バンド表現が `lgirreps` によって返されるすべての異なる **k**-点に投影されるかどうか（`allpaths = false`）、高対称 **k**-線および -平面を含むか、または最大 **k**-点のみに投影されるか（`allpaths = true`）、すなわち高対称点のみに投影されるか。
  * `explicitly_real` (デフォルト: `timereversal`): `timereversal = true` の場合、バンド表現に伴うサイト対称不変表現が明示的に実数である（または「物理的に」実数である）ことを保証するかどうか（[`physical_realify`](@ref)を参照）。これは、時間反転対称性の作用の後続の分析に役立ちます。

## 注意事項

最大ワイコフ位置に関連するすべてのバンド表現が返されます。これは、バンド表現が「複合的」であるかどうかに関係なく、すべてのバンド表現が返されることを意味します。そのため、返されるバンド表現は一般に、基本的なバンド表現の集合のスーパーセットであり（したがって、すべての基本的なバンド表現を含む）、基本的なバンド表現の集合を含みます。

## 実装

実装は、Cano, Bradlyn, Wang, Elcoro らによる [Phys. Rev. B **97**, 035139 (2018)](https://doi.org/10.1103/PhysRevB.97.035139) のセクション II.C-D に基づいています。
