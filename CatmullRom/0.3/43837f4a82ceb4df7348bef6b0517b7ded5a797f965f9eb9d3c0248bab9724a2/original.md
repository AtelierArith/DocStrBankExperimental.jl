```
catmullrom(points, pointsperarc; extend=true)
catmullrom(xs, ys, pointsperarc; extend=true)
catmullrom(xs, ys, zs, pointsperarc; extend=true)
```

Given abcissa-sequenced path of points (as points or as xs and ys), and the number of subdivisions to be fit inbetween pair of points (all neighboring points except the first & last), obtain the centripetal Catmull-Rom splines that cover each segment.    

By default, extrapolated first and final points are affixed to the input point sequence so that all of the input points are present in the resulting sequence (CatmullRom fitting does not include the first and final points). If you prefer this not occur, call the function with `extend=false`.

If you prefer to specify the scale factor used in that extrapolation, use `extendbounds(points, scale=scalefactor)`, and then pass the result to this function with `extend=false`.
