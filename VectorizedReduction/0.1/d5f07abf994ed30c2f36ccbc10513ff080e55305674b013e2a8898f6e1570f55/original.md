```
vtsoftmax(A::AbstractArray)
```

Compute the softmax function, treating the entire array as a single vector. Threaded. Care is taken to ensure that the computation will not overflow/underflow, but the caller should be aware that `+Inf` and `NaN` are not handled.

See also: [`vtlogsoftmax`](@ref)
