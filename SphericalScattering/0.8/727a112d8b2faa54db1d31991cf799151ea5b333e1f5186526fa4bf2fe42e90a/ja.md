```
scatteredfield(sphere::DielectricSphereThinImpedanceLayer, excitation::UniformField, point, quantity::ScalarPotentialJump; parameter::Parameter=Parameter())
```

薄いコーティングを持つ誘電体球体のスカラー電位のジャンプを計算します。このコーティング内の変位場は放射方向のみに存在すると仮定します。与えられた方向に偏光した入射均一場を仮定します。

より正確には、Δ = Φ*i - Φ*eを計算します。ここで、Φ*iは内側のポテンシャル、ϕ*eは外側のポテンシャルです。

点と返される場はデカルト座標系で表されます。
