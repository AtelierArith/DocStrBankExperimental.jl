```
missingsmallest(f)
```

Return a function of two arguments `x` and `y` that tests whether `x` is less than `y` such that `missing` is always less than the other argument. In other  words, return a modified version of the partial order function `f` such that `missing` is the smallest possible value, and all other non-`missing` values are compared according to `f`.

The behavior of the standard `isless` function modified to treat `missing` as the smallest value can be obtained by calling the 2-argument `missingsmallest(x, y)` function. This is equivalent to `missingsmallest(isless)(x, y)`.

# Examples

```
julia> isshorter = missingsmallest((s1, s2) -> isless(length(s1), length(s2)));

julia> isshorter("short", "longstring")
true

julia> isshorter("longstring", "short")
false

julia> isshorter("", missing)
false
```
