```julia
logsumexp!(out, X)

```

Compute [`logsumexp`](@ref) of `X` over the singleton dimensions of `out`, and write results to `out`.

The result is computed in a numerically stable way that avoids intermediate over- and underflow, using a single pass over the data.

See also [`logsumexp`](@ref).

# References

[Sebastian Nowozin: Streaming Log-sum-exp Computation](http://www.nowozin.net/sebastian/blog/streaming-log-sum-exp-computation.html)
