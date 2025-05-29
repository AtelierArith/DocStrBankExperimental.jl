```
mesh(bezierpath::BezierPath,
     colors=Vector{Colors.Colorant})
```

メッシュを作成します。提供された `bezierpath` の最初の3つまたは4つの要素がメッシュ形状の3つまたは4つの辺を定義します。

`colors` 配列は各コーナーポイントの色を定義します。必要に応じて色は再利用されます。少なくとも1つの色を提供する必要があります。

`setmesh()` を使用してメッシュを選択し、形状を塗りつぶすために使用されます。

# 例

```julia
@svg begin
    bp = makebezierpath(ngon(O, 50, 4, 0, vertices=true))
    mesh1 = mesh(bp, [
        "red",
        Colors.RGB(0, 1, 0),
        Colors.RGB(0, 1, 1),
        Colors.RGB(1, 0, 1)
        ])
    setmesh(mesh1)
    box(O, 500, 500, :fill)
end
```
