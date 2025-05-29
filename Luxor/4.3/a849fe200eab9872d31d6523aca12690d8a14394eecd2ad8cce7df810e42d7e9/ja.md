```
polycross(pt::Point, radius, npoints::Int, ratio=0.5, orientation=0.0;
    action      = :none,
    splay       = 0.5,
    vertices    = false,
    reversepath = false)
polycross(pt::Point, radius, npoints::Int, ratio=0.5, orientation=0.0, action;
    splay       = 0.5,
    vertices    = false,
    reversepath = false)
```

`npoints` 本数の腕を持つ十字型の多角形を、`pt` を中心とした半径 `radius` の円の中に作成します。

`ratio` は各腕の二つの側の比率を指定します。`splay` は腕を ... ばらけさせます。

`vertices=true` を使用すると、アクションを実行する代わりに形状の頂点を返します。

（Compose.jl.xgon() から適応）

## 例

```julia
polycross(O, 100, 5,
    action = :fill,
    splay  = 0.5)
```

```julia
polycross(O, 120, 5, 0.5, 0.0, :stroke,
    splay  = 0.5)
```
