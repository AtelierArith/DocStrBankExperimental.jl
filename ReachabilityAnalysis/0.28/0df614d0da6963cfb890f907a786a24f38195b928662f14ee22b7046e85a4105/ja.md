```
DiscreteTransition{RT, GT, IT⁻, IT⁺, WT} <: AbstractTransition
```

離散遷移をエンコードする型で、次のようなアフィン代入の形を持ちます：

$$
    post_d(X) = (R(X ∩ G ∩ I⁻) ⊕ W) ∩ I⁺
$$

ここで、$I⁻$ と $I⁺$ はそれぞれソースとターゲットの位置での不変量、$G ⊆ \mathbb{R}^n$ は遷移のガード集合、代入は $x^+ := Rx + w$ の形を持ち、$w ∈ W$、$x^+ ∈ \mathbb{R}^m$ は遷移後の値、$R ∈ \mathbb{R}^{m\times n}$ は代入マップ（またはリセットマップ）、$W ⊆ \mathbb{R}^m$ は非決定的入力の閉じた有界凸集合です。

### フィールド

  * `R`  – 代入マップ
  * `W`  – 非決定的入力
  * `G`  – ソース位置からターゲット位置への遷移のガード集合
  * `I⁻` – ソース位置での不変量
  * `I⁺` – ターゲット位置での不変量
