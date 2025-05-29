```
r(pnsystem)
separation(pnsystem)
```

Compute the separation between the two black holes.  This is essentially the inverse of [`γₚₙ`](@ref), with some factors of `G` and `M` thrown in.

Note that there should be a factor of `1/c^2` in this expression; we reserve it to use explicitly in PN expansions.  That is, for every factor of `1/r`, we explicitly include a factor of `1/c^2` in the expansion.
