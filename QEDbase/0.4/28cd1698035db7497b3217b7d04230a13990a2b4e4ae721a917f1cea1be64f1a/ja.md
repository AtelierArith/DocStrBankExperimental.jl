```
AbstractInPhaseSpaceLayout <: AbstractPhaseSpaceLayout
```

`AbstractInPhaseSpaceLayout`は、散乱過程における入射粒子の位相空間レイアウトを表します。これは、入射粒子の運動量が位相空間座標からどのように構築されるかを定義します。

## 実装するインターフェース関数:

  * `phase_space_dimension(proc, model, layout::AbstractInPhaseSpaceLayout)`: 入射粒子のための独立した位相空間座標の数を定義します。
  * `_build_momenta(proc, model, in_psl::AbstractInPhaseSpaceLayout, in_coords::Tuple)`: 位相空間座標を使用して入射粒子の運動量を構築します。
