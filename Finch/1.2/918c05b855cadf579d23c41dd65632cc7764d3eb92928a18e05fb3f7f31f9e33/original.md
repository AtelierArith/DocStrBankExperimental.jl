```
maxby(a, b)
```

Return the max of `a` or `b`, comparing them by `a[1]` and `b[1]`, and breaking ties to the left. Useful for implementing argmax operations:

```jldoctest setup=:(using Finch)
julia> a = [7.7, 3.3, 9.9, 3.3, 9.9]; x = Scalar(-Inf => 0);

julia> @finch for i=_; x[] <<maxby>>= a[i] => i end;

julia> x[]
9.9 => 3
```
