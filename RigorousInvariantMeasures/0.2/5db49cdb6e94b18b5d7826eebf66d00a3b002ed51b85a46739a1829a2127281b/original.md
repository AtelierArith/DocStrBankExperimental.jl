```
nonzero_on(B::Hat, dual_element)
```

Return the range of indices of the elements of the basis whose support intersects with the given dual element (i.e., a pair (y, absT')). The range may end with length(B)+1; this must be interpreted "mod length(B)": it means that it intersects with the hat function peaked in 0 as well (think for instance y = 0.9999).
