```
standardize_cell(cell::Cell; to_primitive=false, no_idealize=false, symprec=1e-5)
```

Return standardized cell.

The standardized unit cell is generated from an input unit cell structure and its symmetry found by the symmetry search. The choice of the setting for each space group type is as explained for [`get_dataset`](@ref).
