```julia
GornetDesmorat()
GornetDesmorat(type)

```

# モデル:

$$
W = h_1\int\exp{h_3(I_1-3)^2}\text{d}I_1+3h_2\int\frac{1}{\sqrt{I_2}}\text{d}I_2 = \frac{h_1 \sqrt{\pi} \text{erfi}(\sqrt{h_3}(I_1-3)^2)}{2\sqrt{h_3}}+6h_2\sqrt{I_2}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれかです。

# パラメータ:

  * h₁
  * h₂
  * h₃

# 注意事項:

  * 微分形式は元の形式であり、閉じた形式のSEFはMathematicaでの記号的積分を通じて決定されました。このモデルはADと互換性がなく、第二ピオラ・キルヒホッフ応力テンソルおよびコーシー応力テンソルのメソッドが実装されています。

> Gornet L, Marckmann G, Desmorat R, Charrier P. A new isotropic hyperelastic strain energy function in terms of invariants and its derivation into a pseudo-elastic model for Mullins effect: application to finite element analysis. Constitutive Models for Rubbers VII. 2012:265-71.

