```julia
BoxWedgeTail{T, N, Tt, TA, T2, T3, ZType, F, F2, inplace, RNGType, tolType, spacingType,
    jpdfType, boxType, wedgeType, tailType, distBWTType, distΠType} <:
AbstractNoiseProcess{T, N, Vector{T2}, inplace}
```

GainesとLyonsによる確率的面積積分の乱数生成の方法。この方法は、2次元のMarsagliaの「長方形-くさび-尾」アプローチに基づいています。

ボックスのために3つの異なるグルーピングが実装されています。

  * box_grouping = :Columns（フル、すなわち、drとdaによって広がる正方形上の可能な限り大きい列）
  * box_grouping = :none（グルーピングなし）
  * box_grouping = :MinEntropy（デフォルト、列ごとのグルーピングよりも小さいエントロピーを達成するグルーピングで、したがってわずかに高速なサンプリングを可能にしますが、グループの数はわずかに大きくなります）

サンプリングはDistributions.jlパッケージに基づいており、すなわち、多くの分布の1つからサンプリングするために、Distributions.jlから一変量または二変量の分布が構築され、その後rand(..)が使用されます。

## コンストラクタ

```julia
BoxWedgeTail{iip}(t0, W0, Z0, dist, bridge;
    rtol = 1e-8, nr = 4, na = 4, nz = 10,
    box_grouping = :MinEntropy,
    sqeezing = true,
    save_everystep = true,
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true, reseed = true) where {iip}
```
