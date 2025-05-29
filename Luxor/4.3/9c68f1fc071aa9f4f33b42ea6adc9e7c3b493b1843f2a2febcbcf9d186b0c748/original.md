```
beziersegmentangles(pt1, pt2;
    out = deg2rad(45),
    in  = deg2rad(135),
    l   = 100)
```

Return a BezierPathSegment joining `pt1` and `pt2` making the angles `out` at the start and `in` at the end.

It's similar to the tikZ `(a) to [out=135, in=45] (b)` drawing instruction (but in radians obviously).

`out` is the angle that a line from `pt1` to the outgoing Bézier handle makes with the horizontal. `in` is the angle that a line joining `pt2` from the preceding Bézier handle makes with the horizontal.

The function finds the interesction point of two lines with the two angles and constructs a BezierPathSegment that fits.

See also the `bezierfrompoints()` function that makes a BezierPathSegment that passes through four points.

### Example

```julia
drawbezierpath(beziersegmentangles(O, O + (100, 0),
    out = deg2rad(45),
    in  = 2π - deg2rad(45)),
    :stroke)
```
