```julia
Gregory()
Gregory(type)

```

# モデル:

$$
W = \frac{A}{2-n}(I_1-3+C^2)^{1-\frac{n}{2}}+\frac{B}{2+m}(I_1-3+C^2)^{1+\frac{m}{2}}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `A`
  * `B`
  * `C`
  * `m`
  * `n`

> Gregory IH, Muhr AH, Stephens IJ. Engineering applications of rubber in simple extension. Plastics rubber and composites processing and applications. 1997;26(3):118-22.

