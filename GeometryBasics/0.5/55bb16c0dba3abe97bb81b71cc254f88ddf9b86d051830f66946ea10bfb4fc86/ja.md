```
Tessellation(primitive, nvertices)
```

抽象ジオメトリからメッシュを生成する際、通常は異なる詳細レベル、つまり異なる数の頂点で生成できます。`Tessellation`ラッパーを使用すると、この詳細レベルを指定できます。テッセレーションされたジオメトリからメッシュを生成する際、追加情報は`coordinates`、`faces`などに渡されます。

```julia
sphere = Sphere(Point3f(0), 1)
m1 = mesh(sphere) # テッセレーションのデフォルト値を使用
m2 = mesh(Tessellation(sphere, 64)) # テッセレーションに64を使用
length(coordinates(m1)) != length(coordinates(m2))
```

グリッドベースのテッセレーションの場合、タプルを使用することもできます：

```julia
rect = Rect2(0, 0, 1, 1)
Tessellation(rect, (5, 5))
```
