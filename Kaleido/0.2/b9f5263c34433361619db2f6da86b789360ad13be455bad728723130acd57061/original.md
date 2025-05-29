```
FlatLens(N₁, N₂, ..., Nₙ)
```

# Examples

```jldoctest
julia> using Setfield, Kaleido

julia> l = MultiLens((
           (@lens _.x) ∘ IndexBatchLens(:a, :b, :c),
           (@lens _.y) ∘ IndexBatchLens(:d, :e),
       )) ∘ FlatLens(3, 2);

julia> get((x=(a=1, b=2, c=3), y=(d=4, e=5)), l)
(1, 2, 3, 4, 5)

julia> set((x=(a=1, b=2, c=3), y=(d=4, e=5)), l, (10, 20, 30, 40, 50))
(x = (a = 10, b = 20, c = 30), y = (d = 40, e = 50))
```
