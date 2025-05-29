```
lessthan(x)
```

Return a value which is immediately smaller than `x`. Than value is almost, but not quite, equal to `x` - there should be no other values (of any type) in between `x` and `lessthan(x)` according to Julia's `isless` and `isequal` canonical total ordering.

Amongst other uses, this may be used to create `Interval`s that exclude the end point.

See also `greaterthan`.

# Examples

```julua
julia> isequal(lessthan(10), 10)
false

julia> isless(lessthan(10), 10)
true

julia> 10 ∈ 0..10
true

julia> 10 ∈ 0..lessthan(10)
false
```
