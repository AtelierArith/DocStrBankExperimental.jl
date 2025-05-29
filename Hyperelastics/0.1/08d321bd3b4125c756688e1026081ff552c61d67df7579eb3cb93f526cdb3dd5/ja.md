```julia
NeoHookean()
NeoHookean(type)

```

# モデル:

$$
W = \frac{\mu}{2}(I_1-3)
$$

# 引数

  * `type = PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `μ`: 小ひずみせん断弾性率

> Treloar LR. 長鎖分子のネットワークの弾性—II. ファラデー協会の取引. 1943;39:241-6.

