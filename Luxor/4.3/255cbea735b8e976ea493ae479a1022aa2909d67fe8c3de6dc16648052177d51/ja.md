```
circletangent2circles(radius, circle1center::Point, circle1radius, circle2center::Point, circle2radius)
```

半径 `radius` の最大2つの円の中心を見つけます。これらの円は、`circle1...` と `circle2...` で定義された2つの円に接する必要があります。これらの2つの円は重なっても構いませんが、一方が他方の内部にあってはいけません。

  * (0, O, O)      - そのような円は存在しません
  * (1, pt1, O)    - 1つの円が存在し、pt1を中心としています
  * (2, pt1, pt2)  - 2つの円が存在し、中心はpt1とpt2です

（Oは常に3つの値が返されるようにするためのダミーポイントです。）
