```
skipindex(iterator, skip)
```

`SkipIndexIterator`の作成演算子。

```jldoctest
julia> s = ReactiveMP.skipindex(1:3, 2)
2-element ReactiveMP.SkipIndexIterator{Int64, UnitRange{Int64}}:
 1
 3

julia> collect(s)
2-element Vector{Int64}:
 1
 3
```

関連情報: [`SkipIndexIterator`](@ref)
