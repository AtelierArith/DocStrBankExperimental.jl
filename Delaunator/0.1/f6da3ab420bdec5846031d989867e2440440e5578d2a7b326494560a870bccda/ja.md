```
edgelines(t::Triangulation)
```

三角形分割のエッジを表示するために、Makieのlinesegments関数と一緒に使用できるジェネレーターを返します。各エッジは一度だけ描画されます。

# 例

```
using GLMakie
t = triangulate(rand(StableRNG(1), Point2f, 10))
linesegments(collect(edgelines(rval)))
```
