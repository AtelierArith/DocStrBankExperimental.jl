```
IndexBatchLens(names)
```

# Examples

```jldoctest
julia> using Setfield, Kaleido

julia> lens = IndexBatchLens(:a, :b, :c);

julia> get((a=1, b=2, c=3, d=4), lens)
(1, 2, 3)

julia> set((a=1, b=2, c=3, d=4), lens, (10, 20, 30))
(a = 10, b = 20, c = 30, d = 4)
```
