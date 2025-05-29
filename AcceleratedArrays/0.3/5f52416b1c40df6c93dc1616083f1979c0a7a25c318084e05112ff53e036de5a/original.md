```
greaterthan(x)
```

Return a value which is immediately larger than `x`. Than value is almost, but not quite, equal to `x` - there should be no other values (of any type) in between `x` and `greaterthan(x)` according to Julia's `isless` and `isequal` canonical total ordering.

Amongst other uses, this may be used to create `Interval`s that exclude the starting point.

See also `lessthan`.

# Examples

```julua
julia> isequal(10, greaterthan(10))
false

julia> isless(10, greaterthan(10))
true

julia> 0 ∈ 0..10
true

julia> 0 ∈ greaterthan(0)..10
false
```
