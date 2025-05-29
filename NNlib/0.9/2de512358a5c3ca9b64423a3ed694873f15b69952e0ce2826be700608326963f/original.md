```
logsoftmax(x; dims = 1)
```

Computes the log of softmax in a more numerically stable way than directly taking `log.(softmax(xs))`. Commonly used in computing cross entropy loss.

It is semantically equivalent to the following:

```
logsoftmax(x; dims = 1) = x .- log.(sum(exp.(x), dims = dims))
```

See also [`softmax`](@ref).
