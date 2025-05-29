```
SigmaOnline!{tp}(sigma::Array{tp, 1}, x::AbstractArray{tp, 2}, [Q::AbstractArray{tp, 2}], samplesize::Int = 250, dim::Int = 1)
```

compute `sigma` parameter as mean of the distances of `samplesize` randomly sampled points along `dim`. If Q is given the Mahalanobis distance is used instead of Euclidean.
