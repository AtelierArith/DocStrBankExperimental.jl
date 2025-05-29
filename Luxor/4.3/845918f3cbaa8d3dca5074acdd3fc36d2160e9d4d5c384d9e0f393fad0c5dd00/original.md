```
circlecircleoutertangents(cpt1::Point, r1, cpt2::Point, r2)
```

Return four points, `p1`, `p2,`p3`,`p4`, where a line through`p1`and`p2`, and a line through`p3`and`p4`, form the outer tangents to the circles defined by`cpt1/r1`and`cpt2/r2`.

Returns four identical points (`O`) if one of the circles lies inside the other.
