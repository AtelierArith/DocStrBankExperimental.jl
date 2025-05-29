```julia
Biderman()
Biderman(type)

```

# モデル:

$$
W = \sum\limits_{i,j=0}^{3, 1}C_{i,j}(I_1-3)^i(I_2-3)^j
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()`または`InvariantForm()`のいずれか

# パラメータ:

  * `C10`
  * `C01`
  * `C20`
  * `C30`

> Biderman VL. ゴム部品の計算. Rascheti na prochnost. 1958;40.

