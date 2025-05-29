```
unpack!(A, S; flatten=false) -> A
```

unpacks the non-zero coefficients of the sparse operator `S` into the array `A` and returns `A`.  Keyword `flatten` specifies whether to only consider the length of `A` instead of its dimensions.  In any cases, `A` must have as many elements as `length(S)` and standard linear indexing.

Just call `Array(S)` to unpack the coefficients of a sparse operator `S` without providing the destination array.
