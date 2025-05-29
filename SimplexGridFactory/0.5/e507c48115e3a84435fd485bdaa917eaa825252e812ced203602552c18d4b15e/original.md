```
lineto!(builder, pt)
```

Generate a line from the current pen position to the target point pt, s `moveto!()`, (2D, 3D). pt is either an existing point index or a table of point coordinates. In the latter case, the point is added. It returns index of the target point.

# Example 2D: draw a square with different facetregion numbers

```
 p = moveto!(b,[0,0])
 facetregion!(b,1);  lineto!(b,[1,0])
 facetregion!(b,2);  lineto!(b,[1,1])
 facetregion!(b,3);  lineto!(b,[0,1])
 facetregion!(b,4);  lineto!(b,p)
```

# Example 3D: two planar facet with different facetregion numbers

```
 facetregion!(b,1);
 p1 = moveto!(b,[0,0,0])
 p2 = moveto!(b,[1,0,0])
 p3 = moveto!(b,[1,1,0])
 p4 = moveto!(b,[0,1,0])
 polyfacet!(b,[p1,p2,p3,p4])

 facetregion!(b,2);
 p1 = moveto!(b,[0,0,1])
 p2 = moveto!(b,[1,0,1])
 p3 = moveto!(b,[1,1,1])
 p4 = moveto!(b,[0,1,1])
 polyfacet!(b,[p1,p2,p3,p4])
```
