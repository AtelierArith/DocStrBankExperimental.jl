project(P::Point3D)

3Dポイントを現在の投影によって定義された2D表面に投影します。

TODO 現在、この関数はポイントが視点の後ろにある場合に'nothing'を返します。これにより、変換の処理が少し難しくなりますが、関数は2D Luxorポイントまたは`nothing`のいずれかを返します。

```
using Thebes, Luxor

@svg begin
    eyepoint(Point3D(250, 250, 100))
    centerpoint(Point3D(0, 0, 0))
    uppoint(Point3D(0, 0, 10))
    sethue("grey50")
    carpet(300)
    axes3D(100)
    sethue("red")
    for i in 1:30
        randpoint3D = Point3D(rand(0.0:150, 3)...)
        sethue("red")
        pt1 = pin(randpoint3D)
        if pt1 != nothing
            circle(pt1, 5, :fill)
        end
    end
end
```
