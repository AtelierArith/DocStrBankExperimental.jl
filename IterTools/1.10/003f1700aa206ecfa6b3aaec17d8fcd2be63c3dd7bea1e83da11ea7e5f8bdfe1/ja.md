```
firstrest(xs) -> (f, r)
```

最初の要素と残りのイテレータをタプルとして返します。

関連: `Base.Iterators.peel`。

```jldoctest
julia> f, r = firstrest(1:3);

julia> f
1

julia> collect(r)
2-element Vector{Int64}:
 2
 3
```
