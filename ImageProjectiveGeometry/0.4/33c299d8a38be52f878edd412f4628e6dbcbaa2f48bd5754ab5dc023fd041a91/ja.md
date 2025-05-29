pointinconvexpoly - 2D点が凸多角形内にあるかどうかを判断する

```
Usage:  v = pointinconvexpoly(p, poly)

Arguments:   p - 点を指定する2ベクトル。
          poly - 順番に、時計回りまたは反時計回りに多角形を囲む
                 頂点の系列として定義された凸多角形で、
                 2 x N配列。

Returns:    v - 多角形内の場合は +1
                外部の場合は -1
                 境界上の場合は 0
```

注意: 多角形が実際に凸であるかどうかのチェックはありません。必要に応じてisconvexpoly()を使用してください。

関連情報: isconvexpoly()
