```
Dictionary(indexable)
Dictionary{I}(indexable)
Dictionary{I,T}(indexable)
```

Construct a hash-based dictionary from an indexable input `indexable`, equivalent to `Dictionary(keys(indexable), values(indexable))`. The input might not be copied.

Note: to construct a dictionary from `Pair`s use the `dictionary` function. See also the `index` function.

# Examples

```julia
julia> Dictionary(Dict(:a=>1, :b=>2))
2-element Dictionary{Symbol,Int64}
 :a │ 1
 :b │ 2

julia> Dictionary(3:-1:1)
3-element Dictionary{Int64,Int64}
 1 │ 3
 2 │ 2
 3 │ 1 
```
