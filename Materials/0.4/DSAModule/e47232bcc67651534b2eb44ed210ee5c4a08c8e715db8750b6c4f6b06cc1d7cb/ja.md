```
integrate_material!(material::GenericDSA{T}) where T <: Real
```

動的ひずみ老化（DSA）を持つ材料モデル。このモデルは、運動的および等方的な硬化を伴う二つのバックストレスを持つシャボッシュ材料に似ていますが、このモデルは静的回復項も特徴としています。

このモデルは、動的（および静的）ひずみ老化（DSA）によって引き起こされる硬化を捉えています。関連する現象は以下の通りです：

  * ポルテヴァン・ル・シャトリエ効果。鋸歯状の降伏、塑性不安定性。
  * 不連続降伏
  * 逆ひずみ速度感度（逆SRS）
  * 低サイクル疲労（LCF）試験における二次硬化

これらは通常、特定の温度/ひずみ速度の範囲で発生し、そこでは不純物原子の拡散により転位が固定されます。最も効果的な条件では、拡散速度は適用されたひずみ速度（転位の速度）に匹敵します。

参照：

```
J.-L. Chaboche, A. Gaubert, P. Kanouté, A. Longuet, F. Azzouz, M. Mazière.
Viscoplastic constitutive equations of combustion chamber materials including
cyclic hardening and dynamic strain aging. International Journal of Plasticity
46 (2013), 1--22. http://dx.doi.org/10.1016/j.ijplas.2012.09.011
```

さらなる読み物：

```
M. Mazière, H. Dierke. Investigations on the Portevin Le Chatelier critical
strain in an aluminum alloy. Computational Materials Science 52(1) (2012),
68--72. https://doi.org/10.1016/j.commatsci.2011.05.039
```
