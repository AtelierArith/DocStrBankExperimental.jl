```
AbstractBasis
```

Abstract type for all concrete `Basis` types.  The most important function for a `Basis` type is the index of a given digits and the digits representation of its ith content:

  * `index`  : Return the norm and the index of the digits of the given basis.
  * `change!`: Change the digits to the target index, and return the new normalization.

If we want to calculate the schmidt decomposition (in real space), we can use the `schmidt` function.
