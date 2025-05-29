```
PartialCellBottom(bottom_height; minimum_fractional_cell_height=0.2)
```

Return `PartialCellBottom` representing an immersed boundary with "partial" bottom cells. That is, the height of the bottommost cell in each column is reduced to fit the provided `bottom_height`, which may be a `Field`, `Array`, or function of `(x, y)`.

The height of partial bottom cells is greater than

```
minimum_fractional_cell_height * Δz,
```

where `Δz` is the original height of the bottom cell underlying grid.
