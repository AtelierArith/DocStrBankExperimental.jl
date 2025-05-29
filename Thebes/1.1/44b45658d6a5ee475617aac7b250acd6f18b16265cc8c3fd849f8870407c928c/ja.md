```
make(primitive, name="unnamed")
```

`primitive` には、3Dポイントの配列と、各面が頂点番号のリストである面の配列が含まれています。

Objectを返します。

例

```
make(Cube, "cube")
```

は、頂点の配列、面の配列、およびラベルの配列を含むObjectオブジェクトを返します。

```
@draw begin
    helloworld()
    tol = 0.01
    a = []
    sethue("black")
    for t in -2pi:tol:2pi
        push!(a, Point3D((50 + cos(5t)) * cos(3t), (50 + cos(5t)) * sin(2t), sin(5t)))
    end
    Knot = make((a, []), "knot")
    pin(Knot, gfunction=(args...) -> begin
        for verts in args[1].vertices
            pin(verts)
        end
    end)
end
```

デフォルトのgfunctionは面を期待します - 面がない場合は、頂点を描画するgfunctionを使用してください。
