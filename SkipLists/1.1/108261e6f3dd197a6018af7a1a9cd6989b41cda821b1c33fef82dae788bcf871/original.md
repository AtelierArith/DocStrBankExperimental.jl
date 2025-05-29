```
SkipList{T,M} <: AbstractSkipList{T,M}
```

A non-concurrent skip list. `T` is the type of the element that can be stored in the `SkipList`, while `M` is the list's mode:

  * `M == :List`: the same key can be stored in a skip list multiple times.
  * `M == :Set`: only one copy of each key is allowed in the skip list. `SkipListSet{T}` is an alias for `SkipList{T,:Set}`.

# Examples

```jldoctest; setup = :(using SkipLists)
julia> list = SkipList{Int64}();

julia> insert!(list, 1); insert!(list, 2); insert!(list, 3);

julia> collect(list)
3-element Vector{Int64}:
 1
 2
 3
```
