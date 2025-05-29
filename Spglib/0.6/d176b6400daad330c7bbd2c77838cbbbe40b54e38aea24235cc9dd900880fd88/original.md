```
find_primitive(cell::Cell, symprec=1e-5)
```

Find the primitive cell of an input unit cell.

This function is now a shortcut of `standardize_cell` with `to_primitive = true` and `no_idealize = false`.
