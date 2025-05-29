```julia
HartmannNeff()
HartmannNeff(type)

```

# モデル:

$$
W = \sum\limits_{i,j=0}^{M,N}C_{i,0}(I_1-3)^i -3\sqrt{3}^j+\alpha(I_1-3)
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()`または`InvariantForm()`のいずれか

# パラメータ:

  * `α`
  * `Ci⃗0`
  * `C0j⃗`

> Hartmann S, Neff P. Polyconvexity of generalized polynomial-type hyperelastic strain energy functions for near-incompressibility. International journal of solids and structures. 2003 Jun 1;40(11):2767-91.

