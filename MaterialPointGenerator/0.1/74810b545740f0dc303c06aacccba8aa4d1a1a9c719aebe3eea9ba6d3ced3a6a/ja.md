```
getlongwidth(points; n_segments::Int=200)
```

## 説明:

2次元ポリゴンの最長内部軸（直径）と、それに垂直な最も広い内部軸を計算します。`points`はポリゴンの頂点リストで、関数`getpolygon`（順序付き）によって生成されます。この関数は、最長軸の長さ、その端点、最も広い軸の長さ、およびその端点を返します。

## 例:

```julia
points = [0.0 0.0; 1.0 0.0; 1.0 1.0; 0.0 1.0]
a, b, c, d, e f = getlongwidth(points)
```
