```
minby(a, b)
```

Return the min of `a` or `b`, comparing them by `a[1]` and `b[1]`, and breaking ties to the left. Useful for implementing argmin operations:

```jldoctest setup=:(using Finch)
julia> a = [7.7, 3.3, 9.9, 3.3, 9.9]; x = Scalar(Inf => 0);

julia> @finch for i=_; x[] <<minby>>= a[i] => i end;

julia> x[]
3.3 => 2
```
