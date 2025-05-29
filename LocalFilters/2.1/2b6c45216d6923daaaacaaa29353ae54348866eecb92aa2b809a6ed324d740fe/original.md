```
I = LocalFilters.Indices(A::AbstractArray...)
```

builds a callable object, `I`, that can be used to produce ranges of indices for each of the arrays `A...`. These ranges will all be of the same type: linear index ranges, if all arrays `A...` are vectors, Cartesian index ranges otherwise.

`I` is similar to the `eachindex` method but is specialized for a style of indexing, it can be called as `I(B...)` to yield a suitable index range to access all the entries of array(s) `B...` which are any number of the `A...` specified when building `I`. If `B...` consists in several arrays, they must have the same axes otherwise `I(B...)` will throw a `DimensionMismatch` exception.

Call:

I = LocalFilters.Indices{S}()

with `S = IndexLinear` or `S = IndexCartesian` to specifically choose the indexing style.
