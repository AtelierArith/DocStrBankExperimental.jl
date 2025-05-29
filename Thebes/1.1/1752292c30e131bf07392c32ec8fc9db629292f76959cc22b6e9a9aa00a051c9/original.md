```
pin(o::Object;
    gfunction=(o) -> hiddensurface(o))
```

Draw a rendering of an object.

The default rendering function is `hiddensurface()`.

You can also use the built-in `wireframe()` rendering function.

## Examples

```
@draw begin
    o = make(Cube)
    axes3D(200)
    scaleby!(o, 200, 200, 200)
    eyepoint(250, 270, 300)
    pin(o) # use an attempted hiddensurface rendering

    o = make(Tetrahedron)
    axes3D(200)
    scaleby!(o, 200, 200, 200)
    eyepoint(250, 270, 300)
    pin(o, gfunction=wireframe) # use a wireframe rendering
end
```

## More help

You could write your own rendering function to draw objects.

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
