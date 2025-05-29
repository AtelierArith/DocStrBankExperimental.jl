```
from_moments(::Type{T}, mean, stddev) where {T<:Distribution}
```

Construct a distribution of type `T` using the method of moments. It is assumed that the given `mean` lies within the untransformed support of the distribution.
