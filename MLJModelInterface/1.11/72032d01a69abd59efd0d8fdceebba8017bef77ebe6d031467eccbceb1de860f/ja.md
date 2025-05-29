```
classes(x)
```

`x` と同じプールを持つすべてのカテゴリカル要素（`x` を含む）がリストとして返され、プールに一致した順序で表示されます。ここで `x` は `CategoricalValue` 型であり、`classes(x)` は同じ eltype のベクトルです。`x in classes(x)` は常に真であることに注意してください。

`levels(x.pool)` と混同しないでください。以下の例を参照してください。

```julia-repl
julia> v = categorical(["c", "b", "c", "a"])
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "c"
 "b"
 "c"
 "a"

julia> levels(v)
3-element Vector{String}:
 "a"
 "b"
 "c"

julia> x = v[4]
CategoricalArrays.CategoricalValue{String, UInt32} "a"

julia> classes(x)
3-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "a"
 "b"
 "c"

julia> levels(x.pool)
3-element Vector{String}:
 "a"
 "b"
 "c"
```
