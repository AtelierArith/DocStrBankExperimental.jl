```
AbstractOutPhaseSpaceLayout{IN_PSL<:AbstractInPhaseSpaceLayout} <: AbstractPhaseSpaceLayout
```

`AbstractOutPhaseSpaceLayout`は、散乱過程における出力粒子の位相空間レイアウトを表します。これは通常、入力粒子の位相空間レイアウトに依存し、出力粒子の運動量がそれぞれの座標からどのように構築されるかを指定します。

一般的なパラメータ`IN_PSL`は、出力位相空間レイアウトを入力レイアウトにリンクさせ、過程における二つの構成の整合性を確保します。

## 実装するインターフェース関数:

  * `phase_space_dimension(proc, model, layout::AbstractOutPhaseSpaceLayout)`: 出力粒子のための独立した位相空間座標の数を定義します。
  * `in_phase_space_layout(out_psl::AbstractOutPhaseSpaceLayout)`: 入力と出力の構成の整合性を確保するために関連する入力位相空間レイアウトを提供します。
  * `_build_momenta(proc, model, Ptot::AbstractFourMomentum, out_psl::AbstractOutPhaseSpaceLayout, out_coords::Tuple)`: 出力粒子の運動量を構築し、総入力四運動量に基づいてエネルギーと運動量の保存に従うことを保証します。
