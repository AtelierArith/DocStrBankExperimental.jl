```
FirstOrder{EM} <: AbstractApproximationModel
```

一次の近似モデル。

### フィールド

  * `exp` – （オプション、デフォルト: `BaseExp`）指数法

### アルゴリズム

変換は [LeGuernicG10](@cite):

  * $$
    Φ ← \exp(Aδ)
    $$

    ,
  * $$
    Ω_0 ← CH(\mathcal{X}_0, Φ\mathcal{X}_0 ⊕ δU ⊕ B_ε)
    $$

ここで $B_ε$ は原点を中心とした半径 $ε$ の入力ボールです。
