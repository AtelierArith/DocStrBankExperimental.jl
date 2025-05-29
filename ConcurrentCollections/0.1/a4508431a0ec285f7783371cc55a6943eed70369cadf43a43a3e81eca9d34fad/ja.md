```
maybepop!(collection) -> Some(value::T) または nothing
```

コレクションの末尾から `value` をポップしようとします。非空の場合は `Some(value)` を返します。空の場合は `nothing` を返します。

# 例

```jldoctest maybepop!
julia> using ConcurrentCollections

julia> stack = ConcurrentStack{Int}();

julia> push!(stack, 1);

julia> maybepop!(stack)
Some(1)

julia> maybepop!(stack)  # nothing を返します
```
