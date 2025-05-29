```
box(bbox::BoundingBox;
    action   = :none,
    vertices = false)
box(bbox::BoundingBox, action::Symbol;
    vertices=false)
```

Define a box using the bounds in `bbox`.

Use `vertices = true` to return an array of the four corner points: bottom left, top left, top right, bottom right.
