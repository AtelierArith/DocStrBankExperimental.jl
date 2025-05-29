```
trimbezier(bps::BezierPathSegment, lowpt, highpt)
```

Chop the ends of a BezierPathSegment at `lowpt` and `highpt`. `lowpt` and `highpt` should be between 0 and 1.

Returns a trimmed BezierPathSegment.
