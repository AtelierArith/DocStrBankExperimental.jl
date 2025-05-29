```
offsetpoly(plist::Vector{Point}, d::T) where T<:Number
```

Return a polygon that is offset from a polygon by `d` units.

The incoming set of points `plist` is treated as a polygon, and another set of points is created, which form a polygon lying `d` units away from the source poly.

Polygon offsetting is a topic on which people have written PhD theses and published academic papers, so this short brain-dead routine will give good results for simple polygons up to a point (!). There are a number of issues to be aware of:

  * very short lines tend to make the algorithm 'flip' and produce larger lines
  * small polygons that are counterclockwise and larger offsets may make the new polygon appear the wrong side of the original
  * very sharp vertices will produce even sharper offsets, as the calculated intersection point veers off to infinity
  * duplicated adjacent points might cause the routine to scratch its head and wonder how to draw a line parallel to them
