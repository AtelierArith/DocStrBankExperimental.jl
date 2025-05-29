```
intersectioncirclecircle(cp1, r1, cp2, r2)
```

Find the two points where two circles intersect, if they do. The first circle is centered at `cp1` with radius `r1`, and the second is centered at `cp1` with radius `r1`.

Returns

```
(flag, ip1, ip2)
```

where `flag` is a Boolean `true` if the circles intersect at the points `ip1` and `ip2`. If the circles don't intersect at all, or one is completely inside the other, `flag` is `false` and the points are both Point(0, 0).

Use `intersection2circles()` to find the area of two overlapping circles.

In the pure world of maths, it must be possible that two circles 'kissing' only have a single intersection point. At present, this unromantic function reports that two kissing circles have no intersection points.
