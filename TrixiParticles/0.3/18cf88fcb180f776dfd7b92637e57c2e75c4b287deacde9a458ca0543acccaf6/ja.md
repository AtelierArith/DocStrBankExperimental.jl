```
reset_wall!(rectangular_tank::RectangularTank, reset_faces, positions)
```

タンクの選択された壁は新しい位置に配置されます。

# 引数

  * `reset_faces`: `RectangularTank`[@ref]の`faces`に似た、4（2Dの場合）または6（3Dの場合）次元のブールタプル。
  * `positions`: 新しい位置のタプル

!!! warning
    隣接する壁が同時に内側に移動すると、粒子が重なります。

