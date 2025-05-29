```
mask(point::Point, focus::Point, width, height)
    max = 1.0,
    min = 0.0,
    easingfunction = easingflat)
```

Calculate a value between 0 and 1 for a `point` relative to a rectangular area defined by `focus`, `width`, and `height`. The value will approach `max` (1.0) at the center, and `min` (0.0) at the edges.
