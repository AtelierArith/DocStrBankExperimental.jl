```
point(P::AbstractPath, t::Real)
P(t)
```

Compute the point along path `P` at parameter value `t`. Values of `t` in [k,k+1] correspond to values in [0,1] along curve k of the path, for k = 1,2,...,length(P)-1.

```
point(P::AbstractPath, t::AbstractVector)
```

Vectorize the `point` method for path `P`.
