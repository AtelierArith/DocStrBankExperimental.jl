```
Arc(C, start, delta)
```

Consruct an arc that is the part of the Circle `C` starting at parameter value `start` and ending at `start+delta`. The values are expressed in terms of fractions of a complete circle. The `start` value should be in [0,1), and `delta` should be in [-1,1].

```
Arc(a, b, c)
```

Construct the arc starting at point `a`, passing through `b`, and ending at `c`. If the three points are collinear, a `Segment` is returned instead.
