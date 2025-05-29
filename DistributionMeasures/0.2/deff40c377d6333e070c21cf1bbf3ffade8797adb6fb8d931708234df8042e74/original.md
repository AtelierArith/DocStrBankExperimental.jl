```
struct StandardDist{D<:Distribution{Univariate,Continuous},N} <: Distributions.Distribution{ArrayLikeVariate{N},Continuous}
```

Represents `D()` or a product distribution of `D()` in a dispatchable fashion.

Constructor:

```
    StandardDist{Uniform}(size...)
    StandardDist{Normal}(size...)
```
