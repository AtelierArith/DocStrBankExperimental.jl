```
isempty(collection) -> Bool
```

Determine whether a collection is empty (has no elements).

!!! warning
    `isempty(itr)` may consume the next element of a stateful iterator `itr` unless an appropriate `Base.isdone(itr)` or `isempty` method is defined. Use of `isempty` should therefore be avoided when writing generic code which should support any iterator type.


# Examples

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
