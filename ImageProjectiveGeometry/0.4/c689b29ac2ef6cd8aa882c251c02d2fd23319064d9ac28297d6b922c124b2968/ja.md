homography2d - 2D ホモグラフィを計算します

```
Usage 1:   H = homography2d(x1, x2)

Arguments:
         x1  - 3xN の同次点のセット
         x2  - x1<->x2 となる同次点のセット


Usage 2:    H = homography2d(x)
Argument:
          x  - 単一の引数が供給される場合、それは x = [x1; x2] の形式であると仮定されます

Returns:
         H - x2 = H*x1 となる 3x3 のホモグラフィ
```

Usage 2 は ransac() と共に使用することを意図しています。

このコードは、Hartley と Zisserman の "Multiple View Geometry in Computer Vision" p92 に記載されている正規化された直接線形変換アルゴリズムに従っています。
