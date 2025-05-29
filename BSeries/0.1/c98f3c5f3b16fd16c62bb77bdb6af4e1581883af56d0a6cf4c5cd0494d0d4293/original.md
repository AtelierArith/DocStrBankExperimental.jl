```
renormalize!(series)
```

This function modifies a B-series by dividing each coefficient by the `symmetry` of the corresponding tree.

!!! warning
    This breaks assumptions made on the representation of a B-series. The modified B-series should not be passed to any other function assuming the default normalization.

