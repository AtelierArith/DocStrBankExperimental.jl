```
FirstOrderZonotope{EM} <: AbstractApproximationModel
```

ゾノトープで動作する一次近似モデル。

### フィールド

  * `exp` – （オプション、デフォルト: `BaseExp`）指数法

### アルゴリズム

変換は次の通りです：

  * $$
    Φ ← \exp(Aδ)
    $$

    ,
  * $$
    Ω_0 ← bloat(zono(CH(\mathcal{X}_0, Φ\mathcal{X}_0)), α + β)
    $$

ここで、$bloat(\mathcal{X}, ε)$ は集合 $\mathcal{X}$ を値 $ε$ で膨張させ、$zono(·)$ はその引数をゾノトープで過大評価し、$α$ と $β$ はそれぞれ均質系と入力に対して計算された因子です。

### 参考文献

A. Girard: ゾノトープを用いた不確実線形システムの到達可能性。HSCC 2005.
