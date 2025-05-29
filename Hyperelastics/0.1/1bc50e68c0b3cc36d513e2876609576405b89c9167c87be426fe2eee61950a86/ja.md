```julia
VanDerWaals()
VanDerWaals(type)

```

# モデル:

$$
W = -\mu\{(\lambda_m^2-3)\log(1-\Theta)+\Theta\}-\frac{2\alpha}{3}\bigg(\frac{I-3}{2}\bigg)^{3/2}
$$

ここで:

$$
\Theta = \frac{\beta I_1 + (1-\beta)I_2-3}{\lambda_m^2-3)}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()`または`InvariantForm()`のいずれか。

# パラメータ:

  * μ
  * λm
  * β
  * α

> Kilian HG, Enderle HF, Unseld K. The use of the van der Waals model to elucidate universal aspects of structure-property relationships in simply extended dry and swollen rubbers. Colloid and Polymer Science. 1986 Oct;264(10):866-76. Ambacher H, Enderle HF, Kilian HG, Sauter A. Relaxation in permanent networks. InRelaxation in Polymers 1989 (pp. 209-220). Steinkopff. Kilian HG. A molecular interpretation of the parameters of the van der Waals equation of state for real networks. Polymer Bulletin. 1980 Sep;3(3):151-8.

