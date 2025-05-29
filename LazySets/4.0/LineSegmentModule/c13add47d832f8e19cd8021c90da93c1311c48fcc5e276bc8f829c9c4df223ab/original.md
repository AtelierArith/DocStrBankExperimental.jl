# Extended help

```
constraints_list(L::LineSegment)
```

### Algorithm

$L$ is defined by 4 constraints. In this algorithm, the first two constraints are returned by `halfspace_right` and `halfspace_left`, and the other two are obtained by considering a vector parallel to the line segment passing through one of the vertices.
