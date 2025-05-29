```
delaunay(points, options=Quickhull.Options())
```

`points`のd次元デローニ三角形分割を計算します。`points`は、点のようなオブジェクトのベクター（例：`Tuple`または`StaticVector`）または(D, N)サイズの数値行列であることができます。

三角形分割は(d+1)次元に持ち上げて、凸包を取ることによって見つけられます。
