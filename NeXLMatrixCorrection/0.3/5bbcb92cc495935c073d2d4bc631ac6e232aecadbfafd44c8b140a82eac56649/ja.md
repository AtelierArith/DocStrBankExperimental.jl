```
emitted_intensities(comp::Material, elm::Element, dose::AbstractFloat, e0::AbstractFloat, θtoa::AbstractFloat, Ω::AbstractFloat; mc=XPP, fc=ReedFluorescence)
emitted_intensities(comp::Material, dose::AbstractFloat, e0::AbstractFloat, θtoa::AbstractFloat, Ω::AbstractFloat; mc=XPP, fc=ReedFluorescence)
```

  * comp: 材料の組成
  * elm: イオン化された元素
  * dose: 電子線量 (nA⋅s)
  * e0: ビームエネルギー (eV)
  * θtoa: 離脱角 (ラジアン)
  * Ω: 固体角 (ステラジアン)
  * 特徴的なX線と放出された強度を含むDict{CharXRay, <:AbstractFloat}を返します。

指定された固体角における離脱角からサンプルから放出される強度を計算します。デフォルトではXPPおよびReed蛍光アルゴリズムが使用されますが、単一のシェルからの放出に対して積分Fχが正規化された任意のϕ(ρz)-モデルを使用することができます。
