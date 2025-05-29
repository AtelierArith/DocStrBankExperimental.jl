```
map_expand(map_map::Matrix, pad::Int = 1)
```

Expand a map with padding on each edge to eliminate discontinuities in the discrete Fourier transform. The map is “wrapped around” to make it periodic. Padding expands the map to 7-smooth dimensions, allowing for a faster Fast Fourier Transform algorithm to be used during upward/downward continuation.

**Arguments:**

  * `map_map`: `ny` x `nx` 2D gridded map data
  * `pad`:     minimum padding (grid cells) along map edges

**Returns:**

  * `map_map`: `ny` x `nx` 2D gridded map data, expanded (padded)
  * `padx`:    x-direction padding (grid cells) applied on first edge
  * `pady`:    y-direction padding (grid cells) applied on first edge
