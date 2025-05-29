```
rule(pos, theta;
    boundingbox=BoundingBox(),
    vertices=false)
```

Draw a straight line through `pos` at an angle `theta` from the x axis.

By default, the line spans the entire drawing, but you can supply a BoundingBox to change the extent of the line.

```julia
rule(O)       # draws an x axis
rule(O, pi/2) # draws a  y axis
```

The function:

```julia
rule(O, pi/2, boundingbox=BoundingBox()/2)
```

draws a line that spans a bounding box half the width and height of the drawing. 

Returns the two end points in a Vector.

Use `vertices=true` to just return the end points, without drawing a line.
