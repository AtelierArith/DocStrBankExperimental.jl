```julia
get_x_y_w(bb; threshold, scale)

```

Return an iterator that yields `(x, y, w)` triplets, keeping only `w ≥ threshold`.

When `threshold == 0`, `w`s sum to 1, but this is not maintained. The purpose is to remove outliers for plots, with `threshold = 1e-3` or similar.
