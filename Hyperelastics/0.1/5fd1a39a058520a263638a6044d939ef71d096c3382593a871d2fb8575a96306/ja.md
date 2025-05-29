```julia
EdwardVilgis()

```

# モデル:

$$
W = \frac{1}{2}N_C\Bigg[\frac{(1-\alpha^2)I_1}{1-\alpha^2I_1}+\log(1-\alpha^2I_1)\Bigg]+\frac{1}{2}N_S\Bigg[\sum_{i=1}^{3}\Big\{\frac{(1+\eta)(1-\alpha^2)\lambda_i^2}{( 1+\eta\lambda_i^2)(1-\alpha^2I_1)}+\log(1+\eta\lambda_i^2)\Big\}+\log(1-\alpha^2I_1)\Bigg]
$$

# パラメータ:

  * `Ns`: スリップリンクの数
  * `Nc`: クロスリンクの数
  * `α`: チェーンの非伸縮性の尺度
  * `η`: チェーンのスリップ量の尺度

# 注意:

  * αとηは同じメカニズムから生じるため、ほぼ同じオーダーの大きさであるべきです。両者の間に大きな差がある場合は、最適化アルゴリズムや初期推定に問題がある可能性があります。

> Edwards SF, Vilgis T. The effect of entanglements in rubber elasticity. Polymer. 1986 Apr 1;27(4):483-92.

