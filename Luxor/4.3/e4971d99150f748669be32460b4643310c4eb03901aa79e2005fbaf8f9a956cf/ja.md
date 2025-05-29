```
mesh(points::Array{Point}, colors=Vector{Colors.Colorant})
```

メッシュを作成します。

提供された `points` ポリゴンの最初の三つまたは四つの辺がメッシュ形状の三つまたは四つの辺を定義します。

`colors` 配列は各コーナーポイントの色を定義します。必要に応じて色は再利用されます。少なくとも一つの色を提供する必要があります。

# 例

```julia
@svg begin
    pl = ngon(O, 250, 3, pi/6, vertices=true)
    mesh1 = mesh(pl, [
        "purple",
        Colors.RGBA(0.0, 1.0, 0.5, 0.5),
        "yellow"
        ])
    setmesh(mesh1)
    setline(180)
    ngon(O, 250, 3, pi/6, :strokepreserve)
    setline(5)
    sethue("black")
    strokepath()
end
```
