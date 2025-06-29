```
maybepopfirst!(collection) -> Some(value::T) or nothing
```

Try to pop a `value` from the head of `collection`. Return `Some(value)` if it is non-empty.  Return `nothing` if empty.

# Examples

```jldoctest maybepopfirst!
julia> using ConcurrentCollections

julia> queue = ConcurrentQueue{Int}();

julia> push!(queue, 1);

julia> maybepopfirst!(queue)
Some(1)

julia> maybepopfirst!(queue)  # returns nothing
```
