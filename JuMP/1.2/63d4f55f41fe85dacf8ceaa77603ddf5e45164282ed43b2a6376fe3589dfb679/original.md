```
isequal_canonical(
    aff::GenericAffExpr{C,V},
    other::GenericAffExpr{C,V}
) where {C,V}
```

Return `true` if `aff` is equal to `other` after dropping zeros and disregarding the order. Mainly useful for testing.
