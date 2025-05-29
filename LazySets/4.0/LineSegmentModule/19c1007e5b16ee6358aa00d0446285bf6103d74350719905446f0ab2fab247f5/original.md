# Extended help

```
intersection(LS1::LineSegment, LS2::LineSegment)
```

### Output

A `Singleton`, a `LineSegment`, or an `EmptySet` depending on the result of the intersection.

### Notes

  * If the line segments cross, or are parallel and have a single point in common, that point is returned.
  * If the line segments are parallel and have a line segment in common, that segment is returned.
  * Otherwise, there is no intersection and the empty set is returned.
