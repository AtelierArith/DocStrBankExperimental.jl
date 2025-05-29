```
BoundingBox(str::AbstractString)
```

Return a BoundingBox that just encloses a text string, given the current font selection. Uses the Toy text API (ie `text()` and `textextents()`).

Text is assumed to be placed at the origin (`0/0`).
