```
AbstractTwoBodyInPhaseSpaceLayout <: AbstractInPhaseSpaceLayout
```

高エネルギー物理学における二体システム専用に設計された入射位相空間レイアウトを表す抽象型。この型は、二つの粒子が入射し、散乱または崩壊過程に参加するシナリオに焦点を当てた `AbstractInPhaseSpaceLayout` の特殊なサブタイプです。

`AbstractTwoBodyInPhaseSpaceLayout` の具体的なサブタイプは、二つの入射粒子の運動量のパラメータ化を定義します。例えば、[`Energy`](@ref)、[`Rapidity`](@ref)、または他の運動学的座標によってです。これらのレイアウトは、保存則の下でシステムの位相空間特性を一貫して計算できるようにし、[`QEDbase._build_momenta`](@extref) のような関数でのメソッドディスパッチを容易にします。

この型は、具体的なレイアウトを実装するための基盤として機能し、二体過程が位相空間計算内で柔軟かつ正確にモデル化できることを保証します。

# 関連項目

  * [`QEDbase.AbstractInPhaseSpaceLayout`](@extref): 一般的な入射位相空間レイアウトのためのより広い型。
  * [`AbstractTwoBodyRestSystem`](@ref): 一つの粒子が静止している二体システムを表すサブタイプ。
