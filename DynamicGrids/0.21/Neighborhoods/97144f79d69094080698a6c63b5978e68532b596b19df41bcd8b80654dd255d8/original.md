```
distances(hood::Neighborhood)
```

Get the center-to-center distance of each neighborhood position from the central cell, so that horizontally or vertically adjacent cells have a distance of `1.0`, and a diagonally adjacent cell has a distance of `sqrt(2.0)`.

Vales are calculated at compile time, so `distances` can be used inside rules with little overhead.
