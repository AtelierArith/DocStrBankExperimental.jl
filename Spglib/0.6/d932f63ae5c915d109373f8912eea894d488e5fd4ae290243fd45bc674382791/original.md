```
refine_cell(cell::Cell, symprec=1e-5)
```

Return refined cell.

The standardized crystal structure is obtained from a non-standard crystal structure which may be slightly distorted within a symmetry recognition tolerance, or whose primitive vectors are differently chosen, etc. This function is now a shortcut of `standardize_cell` with `to_primitive = false` and `no_idealize = false`.
