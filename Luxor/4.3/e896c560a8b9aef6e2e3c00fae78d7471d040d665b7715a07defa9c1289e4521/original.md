```
splitbezier(bps::BezierPathSegment, t)
```

Split the Bezier path segment at t, where t is between 0 and 1.

Use Paul de Casteljaus' algorithm (the man who really introduced Bezier curves...).

Returns a tuple of two BezierPathSegments, the 'lower' one (0 to `t`) followed by the 'higher' one (`t` to 1).

## Example

```julia-repl
julia> bps = BezierPathSegment(ngon(O, 200, 4, vertices=true)...)
4-element BezierPathSegment:
 Point(1.2246467991473532e-14, 200.0)
 Point(-200.0, 2.4492935982947064e-14)
 Point(-3.6739403974420595e-14, -200.0)
 Point(200.0, -4.898587196589413e-14)

julia> l, h = splitbezier(bps::BezierPathSegment, 0.5)
(Point[Point(1.2246467991473532e-14, 200.0), Point(-100.0, 100.00000000000001), Point(-100.0, 1.4210854715202004e-14), Point(-50.00000000000001, -49.99999999999999)], Point[Point(-50.00000000000001, -49.99999999999999), Point(-1.4210854715202004e-14, -100.0), Point(99.99999999999999, -100.00000000000003), Point(200.0, -4.898587196589413e-14)])

julia> h
4-element BezierPathSegment:
 Point(-50.00000000000001, -49.99999999999999)
 Point(-1.4210854715202004e-14, -100.0)
 Point(99.99999999999999, -100.00000000000003)
 Point(200.0, -4.898587196589413e-14)

julia> l.p2 == h.p1
true
```
