```
integrate_material!(material::GenericChabocheThermal{T}) where T <: Real
```

熱効果を持つシャボッシュ粘塑性材料。モデルには、3つのバックストレスを持つ運動硬化と等方硬化が含まれています。

プライム（'）は時間微分を示します。進化方程式は次のとおりです：

σ' = D : εel' + dD/dθ : εel θ'   R' = b (Q - R) p'   Xj' = ((2/3) Cj n - Dj Xj) p'   (和はなし)

ここで j = 1, 2, 3 です。ひずみは弾性、熱、粘塑性の寄与から成ります：

ε = εel + εth + εpl

弾性領域の外では、粘塑性ひずみ応答は次のように与えられます：

εpl' = n p'

ここで

n = ∂f/∂σ

および p' はノートン-ベイリーのべき法則に従います：

p' = 1/tvp * (<f> / Kn)^nn

ここで <...> はマカウレイ括弧（すなわち正の部分）であり、降伏基準はフォン・ミーゼス型です：

f = √(3/2 dev(σ*eff) : dev(σ*eff)) - (R0 + R)   σ_eff = σ - ∑ Xj

参照：

```
J.-L. Chaboche. 構成方程式のサイクリックプラスティシティとサイクリック
粘塑性. International Journal of Plasticity 5(3) (1989), 247--302.
https://doi.org/10.1016/0749-6419(89)90015-6
```

さらなる読み物：

```
J.-L. Chaboche. 一部の塑性および粘塑性構成理論のレビュー. International Journal of Plasticity 24 (2008), 1642--1693.
https://dx.doi.org/10.1016/j.ijplas.2008.03.009

J.-L. Chaboche, A. Gaubert, P. Kanouté, A. Longuet, F. Azzouz, M. Mazière.
サイクリック硬化と動的ひずみ老化を含む燃焼室材料の粘塑性構成方程式. International Journal of Plasticity
46 (2013), 1--22. https://dx.doi.org/10.1016/j.ijplas.2012.09.011
```
