```
mask(point::Point, focus::Point, radius)
    max = 1.0,
    min = 0.0,
    easingfunction = easingflat)
```

Calculate a value between 0 and 1 for a `point` relative to a circular area defined by `focus` and `radius`. The value will approach `max` (1.0) at the center of the circular area, and `min` (0.0) at the circumference.
