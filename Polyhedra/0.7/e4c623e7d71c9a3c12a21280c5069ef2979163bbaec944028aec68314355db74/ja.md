```
vrep(points::PointIt, lines::LineIt, rays::RayIt;
     d = Polyhedra.FullDim_rec(points, lines, rays))
```

与えられた点 `points` の凸包と線 `lines` および光線 `rays` の円錐包のミンコフスキー和に等しい次元 `d` のフル次元ポリヘドロンの V 表現を作成します。
