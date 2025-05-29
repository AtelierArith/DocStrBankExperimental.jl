```
XPRS_EXTRASETELEMS
```

The initial number of extra elements in sets to allow for in the matrix. (integer)

If sets are to be added to the matrix, then, for maximum efficiency, space should be reserved for the set elements before the matrix is input by setting the `EXTRASETELEMS` control. If this is not done, resizing will occur automatically, but more space may be allocated than the user actually requires.

Default value: `0`

Domain: 0~+INF
