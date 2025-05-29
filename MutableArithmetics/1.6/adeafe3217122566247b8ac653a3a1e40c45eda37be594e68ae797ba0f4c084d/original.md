```
isequal_canonical(a, b)
```

Return whether `a` and `b` represent a same object, even if their representations differ.

## Examples

The terms in two MathOptInterface affine functions may not match but once the duplicates are merged, the zero terms are removed and the terms are sorted in ascending order of variable indices (i.e. their canonical representation), the equality of the representation is equivalent to the equality of the objects begin represented.
