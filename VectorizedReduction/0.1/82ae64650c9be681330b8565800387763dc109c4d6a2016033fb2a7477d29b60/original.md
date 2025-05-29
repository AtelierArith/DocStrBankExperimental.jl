```
vlogsoftmax(A::AbstractArray)
```

Compute the log of the softmax function, treating the entire array as a single vector. Care is taken to ensure that the computation will not overflow/underflow, but the caller should be aware that `+Inf` and `NaN` are not handled.

See also: [`vsoftmax`](@ref)
