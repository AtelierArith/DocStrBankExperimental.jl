```
AbstractOutPhaseSpaceLayout{IN_PSL<:AbstractInPhaseSpaceLayout} <: AbstractPhaseSpaceLayout
```

`AbstractOutPhaseSpaceLayout`は、散乱過程における出力粒子の位相空間レイアウトを表します。これは通常、入力粒子の位相空間レイアウトに依存し、出力粒子の運動量がそれぞれの座標からどのように構築されるかを指定します。

汎用パラメータ`IN_PSL`は、出力位相空間レイアウトを入力レイアウトにリンクさせ、プロセス内の2つの構成の間で一貫性を持たせます。

## 実装するインターフェース関数:

  * `phase_space_dimension(proc, model, layout::AbstractOutPhaseSpaceLayout)`: 出力粒子のための独立した位相空間座標の数を定義します。
  * `in_phase_space_layout(out_psl::AbstractOutPhaseSpaceLayout)`: 入力と出力の構成の間で一貫性を確保するために、関連する入力位相空間レイアウトを提供します。
  * `_build_momenta(proc, model, Ptot::AbstractFourMomentum, out_psl::AbstractOutPhaseSpaceLayout, out_coords::Tuple)`: 出力粒子の運動量を構築し、総入力四運動量に基づいてエネルギーと運動量の保存に準拠することを保証します。
