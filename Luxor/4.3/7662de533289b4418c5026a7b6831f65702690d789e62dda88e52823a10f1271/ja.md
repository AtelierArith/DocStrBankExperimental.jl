```
circlepointtangent(through::Point, radius, targetcenter::Point, targetradius)
```

点 `through` を通り、半径 `targetradius` で中心 `targetcenter` の円に接する半径 `radius` の円の中心を最大2つ見つけます。

この関数はタプルを返します：

  * (0, O, O)      - 円は存在しません
  * (1, pt1, O)    - 1つの円が存在し、中心は pt1 にあります
  * (2, pt1, pt2)  - 2つの円が存在し、中心は pt1 と pt2 にあります

（O は常に3つの値が返されるようにするためのダミーポイントです。）
