```
pin(o::Object;
    gfunction=(o) -> hiddensurface(o))
```

オブジェクトのレンダリングを描画します。

デフォルトのレンダリング関数は `hiddensurface()` です。

組み込みの `wireframe()` レンダリング関数を使用することもできます。

## 例

```
@draw begin
    o = make(Cube)
    axes3D(200)
    scaleby!(o, 200, 200, 200)
    eyepoint(250, 270, 300)
    pin(o) # 試みた hiddensurface レンダリングを使用

    o = make(Tetrahedron)
    axes3D(200)
    scaleby!(o, 200, 200, 200)
    eyepoint(250, 270, 300)
    pin(o, gfunction=wireframe) # wireframe レンダリングを使用
end
```

## さらなるヘルプ

オブジェクトを描画するための独自のレンダリング関数を書くことができます。

```
function a_rendering_function(o::Object)
   if !isempty(o.faces)
       sortfaces!(o)
       @layer begin
           for (n, face) in enumerate(o.faces)
               @layer begin
                   vertices = o.vertices[face]
                   sn = surfacenormal(vertices)
                   ang = anglebetweenvectors(sn, eyepoint())
                   setgrey(rescale(ang, 0, π, 1, 0))
                   pin(vertices, gfunction = (p3, p2) ->
                    begin
                       poly(p2, :fill)
                       sethue("white")
                       poly(p2, :stroke, close=true)
                    end)
               end
           end
       end
   end
end
```
