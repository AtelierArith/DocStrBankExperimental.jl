```
index(b::TranslationalBasis)
```

Index of the state in `TranslationalBasis`, together with the normalization.

## Outputs:

  * `N`: Normalization for the state `b.dgt`.
  * `i`: Index for the state `b.dgt`.

## Notes:

To calculate the index of a given digits, we first shift the digits to that of the minimum index, then search for the place in the basis. Because of the restriction from the momentum, some state with zero normalization (which is not included in the basis) will appear. To avoid exception in the matrix constructon of `Operation`, we allow the index to not in the basis content. When this happend, we return index 1, and normalization 0, so it has no effect on the matrix being filled.
