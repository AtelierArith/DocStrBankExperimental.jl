```
standardize(cryst::Crystal; idealize=true)
```

Return the symmetry-inferred standardized crystal unit cell. If `idealize=true`, then the lattice vectors and site positions will be adapted. See "definitions and conventions" of the [spglib documentation](https://spglib.readthedocs.io/en/stable/) for more information.
