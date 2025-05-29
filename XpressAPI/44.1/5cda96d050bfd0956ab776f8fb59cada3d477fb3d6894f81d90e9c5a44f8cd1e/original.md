```
XPRS_EXTRAELEMS
```

The initial number of extra matrix elements to allow for in the matrix, including coefficients for cuts. (integer)

If rows or columns are to be added to the matrix, then, for maximum efficiency, space should be reserved for the extra matrix elements before the matrix is input by setting the `EXTRAELEMS` control. If this is not done, resizing will occur automatically, but more space may be allocated than the user actually requires.

Default value: Hardware/platform dependent.

Domain: 0~+INF
