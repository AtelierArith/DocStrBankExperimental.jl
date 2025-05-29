```
 getpart(mx::Mxpr,ind1::Integer,ind2::Integer,...)
```

return part of expression `mx`. `ind1,...` indices into `mx`. An index value `0` refers to the head of `mx` or a subexpression, that is the part returned by `mhead`. Index values greater than `0` refer to elements.

Note that `0` only makes sense as the last index.

Negative indices are not supported here. That is, we assume they have already been converted to positive
