```
mean(A::AbstractArray, w::AbstractWeights[, dims::Int])
```

Compute the weighted mean of array `A` with weight vector `w` (of type `AbstractWeights`). If `dim` is provided, compute the weighted mean along dimension `dims`.

# Examples

```julia
n = 20
x = rand(n)
w = rand(n)
mean(x, weights(w))
```
