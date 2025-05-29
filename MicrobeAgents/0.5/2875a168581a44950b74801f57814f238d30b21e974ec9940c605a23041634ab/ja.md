```
BrownBerg{D} <: AbstractMicrobe{D}
```

'Brown and Berg (1974) PNAS' の化学走行性E.coliモデル

デフォルトパラメータ:

  * `motility = RunTumble(0.67, [30.0], Isotropic(D), 0.1)`
  * `rotational_diffusivity = 0.035` rad²/s ブラウン運動の回転拡散の係数
  * `radius = 0.5` μm 微生物の等価球半径
  * `state = 0.0` 論文中の「加重dPb/dt」に対応
  * `gain = 660` s
  * `receptor_binding_constant = 100` μM
  * `memory = 1` s
