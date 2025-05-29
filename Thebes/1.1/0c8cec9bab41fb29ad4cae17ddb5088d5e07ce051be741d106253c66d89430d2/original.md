```
objecttopoly(o::Object)
```

Return a tuple:

  * an array of 2D points representing the vertices of `o`
  * an array of 2D polygons representing the faces of `o`

## Example

This example draws the faces of a cube in colors, and marks the vertices in black.

```
using Luxor, Thebes

@draw begin
    helloworld()
    o = make(Cube)
    scaleby!(o, 100, 100, 100)
    vs, fs = objecttopoly(o)
    setopacity(0.4)
    sethue("black")
    for face in fs
        randomhue()
        poly(face, :fill)
    end
    sethue("black")
    circle.(vs, 3, :fill)
end
```
