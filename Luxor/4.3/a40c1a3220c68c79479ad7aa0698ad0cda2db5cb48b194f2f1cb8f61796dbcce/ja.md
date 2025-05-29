```
star(center, radius, npoints, ratio=0.5, orientation, action=:none;
    vertices = false, reversepath=false)
star(center, radius, npoints, ratio=0.5, orientation=0.0;
    action=:none, vertices = false, reversepath=false)
```

`center`を中心に、`npoints`のセクションを`orientation`に沿って持つ星を作成します。`ratio`は、星の大きい半径に対する小さい半径の高さを指定します。

星の頂点を返します。

`vertices=true`を使用すると、星を作成するのではなく、星の頂点のみを返します。

## 例

```julia
star(O, 120, 5, 0.5, 0.0, :fill,
    vertices = false,
    reversepath=false)
```

```julia
star(O, 220, 5, 0.5;
    action=:stroke,
    vertices = false,
    reversepath=false)
```
