```
maybepopfirst!(collection) -> Some(value::T) または nothing
```

コレクションの先頭から `value` をポップしようとします。コレクションが空でない場合は `Some(value)` を返します。空の場合は `nothing` を返します。

# 例

```jldoctest maybepopfirst!
julia> using ConcurrentCollections

julia> queue = ConcurrentQueue{Int}();

julia> push!(queue, 1);

julia> maybepopfirst!(queue)
Some(1)

julia> maybepopfirst!(queue)  # nothing を返す
```
