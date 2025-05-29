```
CannonballFixedDrag(radius::Number, mass::Number, drag_coeff::Number)
```

固定された弾道係数ドラッグモデルのためのコンストラクタ。

弾道係数は次の式で計算されます：

```
            BC = CD * area/mass
```

ここで、areaは球の2D投影です。

```
            area = π * r^2
```

# 引数

  * `radius::Number`: 宇宙船の半径。
  * `mass::Number`: 宇宙船の質量。
  * `drag_coeff::Number`: 宇宙船の抗力係数。

# 戻り値

  * `drag_model::CannonballFixedDrag`: 固定された弾道係数ドラッグモデル。
