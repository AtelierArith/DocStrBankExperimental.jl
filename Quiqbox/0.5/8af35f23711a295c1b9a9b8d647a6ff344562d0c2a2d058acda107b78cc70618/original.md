```
BasisFuncs{T, D, 𝑙, GN, PT, ON} <: FloatingGTBasisFuncs{T, D, 𝑙, GN, PT, ON}
```

A collection of basis functions with identical parameters except having different  orientations within a specified subshell (i.e. same total orbital angular momentum). It has  the same fields as `BasisFunc`. Specifically, for `l`, its size `ON` can be no less than 1  and no larger than the size of the corresponding subshell.
