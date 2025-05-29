```
get_smallest_interval_edges(
    samples::DensitySampleVector, 
    key::Union{Symbol, Real}, 
    p::Real; 
    bins=200,
    atol=0.0)
```

Calculates the edges of the smallest intervals containing the fraction `p` of the probability of the marginal distribution of parameter `key`.

Returns a `NamedTuple` with the keys `lower` and `upper` which both contain `Vector`s with the corresponding bin edges. Keywords:

  * `bins=200`: The number of bins used fpr calculating the intervals and edges.
  * `atol=0.0`: Intervals are joined together when they are seperated by less than this value.
