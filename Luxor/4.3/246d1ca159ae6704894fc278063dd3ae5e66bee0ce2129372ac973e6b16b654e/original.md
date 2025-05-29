```
circlecircleinnertangents(circle1center::Point, circle1radius, circle2center::Point, circle2radius)
```

Find the inner tangents of two circles. These are tangent lines that cross as they skim past one circle and touch the other.

Returns the four points: tangentpoint1 on circle 1, tangentpoint1 on circle2, tangentpoint2 on circle 1, tangentpoint2 on circle2.

Returns `(O, O, O, O)` if inner tangents can't be found (eg when the circles overlap).

Use `circlecircleoutertangents()` to find the outer tangents.
