```julia
Amin()
Amin(type)

```

# モデル:

$$
W = C_1 (I_1 - 3) + \frac{C_2}{N + 1} (I_1 - 3)^{N + 1} + \frac{C_3}{M + 1} (I_1 - 3)^{M + 1} + C_4 (I_2 - 3)
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれかです。

# パラメータ:

  * `C1`
  * `C2`
  * `C3`
  * `C4`
  * `N`
  * `M`

> Amin AF, Wiraguna SI, Bhuiyan AR, Okui Y. 圧縮およびせん断における自然および高ダンピングゴムの有限要素解析のための超弾性モデル. 工学力学ジャーナル. 2006年1月;132(1):54-64.

