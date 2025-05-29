```julia
HorganSaccomandi()
HorganSaccomandi(type)

```

# モデル:

$$
W = -\frac{\mu J}{2}\log\bigg(\frac{J^3-J^2I_1+JI_2-1}{(J-1)^3}\bigg)
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `μ`
  * `J`

> Horgan CO, Saccomandi G. 限界チェーン伸長性を持つ圧縮性非線形弾性材料のための構成モデル. Journal of Elasticity. 2004年11月;77(2):123-38.> Horgan CO, Saccomandi G. アタクティックエラストマーのための構成モデル. InWaves And Stability In Continuous Media 2004 (pp. 281-294).

