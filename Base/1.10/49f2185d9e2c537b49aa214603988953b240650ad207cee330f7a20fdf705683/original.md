```
collect(collection)
```

Return an `Array` of all items in a collection or iterator. For dictionaries, returns `Vector{Pair{KeyType, ValType}}`. If the argument is array-like or is an iterator with the [`HasShape`](@ref IteratorSize) trait, the result will have the same shape and number of dimensions as the argument.

Used by comprehensions to turn a generator into an `Array`.

# Examples

```jldoctest
julia> collect(1:2:13)
7-element Vector{Int64}:
  1
  3
  5
  7
  9
 11
 13

julia> [x^2 for x in 1:8 if isodd(x)]
4-element Vector{Int64}:
  1
  9
 25
 49
```
