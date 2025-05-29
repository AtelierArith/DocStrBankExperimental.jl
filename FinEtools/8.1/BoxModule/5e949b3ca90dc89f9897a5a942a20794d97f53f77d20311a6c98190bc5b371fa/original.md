```
intersectboxes(box1::AbstractVector, box2::AbstractVector)
```

Compute the intersection of two boxes.

The function returns an empty box (length(b) == 0) if the intersection is empty; otherwise a box is returned.
