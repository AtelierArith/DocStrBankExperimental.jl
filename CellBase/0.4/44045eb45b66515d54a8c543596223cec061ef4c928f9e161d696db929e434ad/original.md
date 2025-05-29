```
Cell(cell::SCell)
```

Return a `Cell` object from `Spglib.Cell` where the `SCell.types` have been changed to 1-based index. This is useful when the `Spglib._expand_cell` is called where the `types` returned is re-indexed.
