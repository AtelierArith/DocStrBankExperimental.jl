```
push(collection, items...)
```

Return a new collection containing all elements of `collection` and of `items`.

# Examples

```jldoctest
julia> s = DigitSet([4, 9]);

julia> push(s, 1, 11)
DigitSet with 4 elements:
  1
  4
  9
  11
```
