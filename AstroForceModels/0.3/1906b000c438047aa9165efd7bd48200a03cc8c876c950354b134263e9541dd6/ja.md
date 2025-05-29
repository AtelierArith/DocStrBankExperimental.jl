```
CannonballFixedSRP(radius::Number, mass::Number, drag_coeff::Number)
```

固定された弾道係数SRPモデルのためのコンストラクタ。

弾道係数は次の式で計算されます：

```
            RC = CD * area/mass
```

ここで、areaは球の2D投影です。

```
            area = π * r^2
```

# 引数

  * `radius::Number`: 宇宙船の半径。
  * `mass::Number`: 宇宙船の質量。
  * `reflectivity_coeff::Number`: 宇宙船の反射係数。

# 戻り値

  * srp_model::CannonballFixedSRP`: 固定された弾道係数SRPモデル。
