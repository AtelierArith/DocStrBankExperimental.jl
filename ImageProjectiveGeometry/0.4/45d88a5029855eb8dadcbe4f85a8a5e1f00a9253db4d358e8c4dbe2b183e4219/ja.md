convexpolyintersect - 凸多角形が交差する場合はtrueを返します。

```
Usage:  intersect = convexpolyintersect(p1, p2) 

Arguments:  p1, p2 - テストされる2つの凸多角形で、これらの多角形は
                     多角形の周りの頂点座標の2xN配列として定義されます。

Returns:             ブール値の結果。
```

注意: 多角形が実際に凸であるかどうかのチェックは行われません。必要に応じてisconvexpoly()を使用してください。

関連情報: isconvexpoly(), rectintersect()
