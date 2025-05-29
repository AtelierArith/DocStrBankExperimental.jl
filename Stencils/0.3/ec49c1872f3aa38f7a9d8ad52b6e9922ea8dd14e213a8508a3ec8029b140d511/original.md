```
distances(hood::Stencil)
```

Returns an `SVector` of center-to-center distance of each stencil position from the central cell, so that horizontally or vertically adjacent cells have a distance of `1.0`, and a diagonally adjacent cell has a distance of `sqrt(2.0)`.

Values are calculated at compile time, so `distances` can be used with little overhead.
