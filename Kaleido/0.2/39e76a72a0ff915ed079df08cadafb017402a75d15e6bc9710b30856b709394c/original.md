```
KeyBatchLens(names)
```

# Examples

```jldoctest
julia> using Setfield, Kaleido

julia> lens = KeyBatchLens(:a, :b, :c);

julia> get((a=1, b=2, c=3, d=4), lens)
(a = 1, b = 2, c = 3)

julia> set((a=1, b=2, c=3, d=4), lens, Dict(:a=>10, :b=>20, :c=>30))
(a = 10, b = 20, c = 30, d = 4)
```
