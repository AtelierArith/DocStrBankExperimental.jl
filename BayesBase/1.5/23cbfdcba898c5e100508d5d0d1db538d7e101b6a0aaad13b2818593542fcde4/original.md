```
ProductOf
```

A generic structure representing a product of two distributions.  Can be viewed as a tuple of `(left, right)`.  Does not check nor supports neither variate forms during the creation stage. Uses the `fuse_support` function to fuse supports of two different distributions.

This object does not define any statistical properties (such as `mean` or `var` etc) and cannot be used as a distribution explicitly. Instead, it must be further approximated as a member of some other distribution. 

See also: [`prod`](@ref), [`GenericProd`](@ref), [`fuse_supports`](@ref)
