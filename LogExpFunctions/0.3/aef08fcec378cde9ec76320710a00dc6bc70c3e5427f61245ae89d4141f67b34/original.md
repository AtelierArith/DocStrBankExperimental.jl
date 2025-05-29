```julia
logsumexp(X)

```

Compute `log(sum(exp, X))`.

`X` should be an iterator of real or complex numbers. The result is computed in a numerically stable way that avoids intermediate over- and underflow, using a single pass over the data.

See also [`logsumexp!`](@ref).

# References

[Sebastian Nowozin: Streaming Log-sum-exp Computation](http://www.nowozin.net/sebastian/blog/streaming-log-sum-exp-computation.html)
