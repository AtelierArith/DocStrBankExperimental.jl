```
simplexgrid(X; bregions=[1,2],cellregion=1)
```

Constructor for 1D grid.

Construct 1D grid from an array of node coordinates. It creates two boundary regions with index 1 at the left end and index 2 at the right end by default.

The keyword arguments allow to overwrite the default region numbers.

Primal grid holding unknowns: marked by `o`, dual grid marking control volumes: marked by `|`.

```@raw html
 o-----o-----o-----o-----o-----o-----o-----o-----o
 |--|-----|-----|-----|-----|-----|-----|-----|--|
```
