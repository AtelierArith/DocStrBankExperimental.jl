```
qmglmesh(data::Array{Float64, 2}, xMin = -10.0, xMax = 10.0, yMin = -10.0, yMax = 10.0,  style::String = ""; name = "", type = 0)
```

draw a 3D mesh/surface.   Currently works only for Linux (is this true?). 
 data - vertical (z) coordinates of the surface. should be Array{Float64, 2}
xMin, xMax, yMin, yMax is the definition of the range where to draw a surface. All the  coordinates from 'data' are evenly distributed inside this range.
style how to draw the surface. Some hints could be taken from here: http://mathgl.sourceforge.net/doc_en/Color-scheme.html 
type  -   0 or 1;  mesh/grid  or surface
name - not used yet (maybe will add later)
