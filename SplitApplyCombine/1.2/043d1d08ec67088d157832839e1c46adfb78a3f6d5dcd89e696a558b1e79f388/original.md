```
grouponly([by], [f], iter)
```

Return a dictionary mapping the unique elements `x` of iter grouped by `by(x)` with value `f(x)`, where `by` and `f` default to the identity function.

This is an optimized equivalent of `only.(group(by, f, iter))` and is similar to `Dictionary(by.(iter), f.(iter))`
