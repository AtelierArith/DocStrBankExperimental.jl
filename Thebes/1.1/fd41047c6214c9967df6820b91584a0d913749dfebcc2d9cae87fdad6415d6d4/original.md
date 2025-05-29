project(P::Point3D)

Project a 3D point onto a 2D surface, as defined by the current projection.

TODO Currently this returns 'nothing' if the point is behind the eyepoint. This makes handling the conversion a bit harder, though, since the function now returns either a 2D Luxor point or `nothing`.

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
