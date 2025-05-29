```
intersectionlines(p0, p1, p2, p3;
    crossingonly=false)
```

Find the point where two lines intersect.

Return `(resultflag, resultip)`, where `resultflag` is a Boolean, and `resultip` is a Point.

If `crossingonly == true` the point of intersection must lie on both lines.

If `crossingonly == false` the point of intersection can be where the lines meet if extended almost to 'infinity'.

Accordng to this function, collinear, overlapping, and parallel lines never intersect. Ie, the line segments might be collinear but have no points in common, or the lines segments might be collinear and have many points in common, or the line segments might be collinear and one is entirely contained within the other.

If the lines are collinear and share a point in common, that is the intersection point.
