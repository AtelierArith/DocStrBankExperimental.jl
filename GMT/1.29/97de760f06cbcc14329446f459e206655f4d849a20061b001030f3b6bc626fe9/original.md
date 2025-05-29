```
mosaic([zoom::Int=??])
```

Print a table with the zoom level characteristics in terms of tile sizes, resolutions, typical use.

If the `zoom` option is used then the table is printed with that zoom level only.

# Example

```jldoctest
julia> mosaic(zoom=10)
┌───────┬────────────────┬────────────┬────────────────┬────────────────────┐
│ Level │     Tile width │  m / pixel │         ~Scale │        Examples of │
│       │ ° of longitude │ on Equator │                │ areas to represent │
├───────┼────────────────┼────────────┼────────────────┼────────────────────┤
│    10 │          0.352 │    153.054 │ 1:500 thousand │  metropolitan area │
└───────┴────────────────┴────────────┴────────────────┴────────────────────┘
```
