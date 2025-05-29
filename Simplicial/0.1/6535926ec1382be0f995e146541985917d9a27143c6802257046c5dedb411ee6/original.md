```
simplexmap(C; check_complete=true, check_max=true)
```

Returns an integer `m` and array `T` of subsets such that `C == trunksmorphism(delta(m),T)`. Because checking if `C` is intersection-complete and/or checking if it has a unique maximal element is potentially time-consuming, the keyword arguments can be used to skip these checks.

`check_complete = false` will skip computing the intersection completion of `C` and assume `C` is already intersection-complete; no guarantee what will be returned in this case.

`check_max = false` will skip checking if `C` has a unique maximal codeword. Again, if `C` does not already have a unique maximal codeword, no guarantee what will be returned in this case.
