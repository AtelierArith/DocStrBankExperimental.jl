```
ellipse(centerpoint::Point, w, h; action=:none)
ellipse(centerpoint::Point, w, h; action)
```

Make an ellipse, centered at `centerpoint`, with width `w`, and height `h`, and add it to the current path.

Returns a tuple of two points, the corners of a bounding box that encloses the ellipse.

See also: `circle()`, `squircle()`, `ellipseinquad()`...
