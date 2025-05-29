```
tally(data; kw...)
```

Construct a tally by considering all elements of `data`, which can be any iteratable object.

# Keyword arguments

  * `by`: By default, elements themselves are compared when doing the counting. If `by = f` is provided, than the elements `(f(k) for k in it)` will be counted.
  * `equivalence`: By default, elements are compared using the `isequal` function. This can be overwritten by providing a 2-ary boolean function `equivalence`.
  * `use_hash`: Enable the use of hashing. This assumes that the elements that are counted have a consistent `hash` implementation. Use this if you want the function to go faster.

# Examples

```jldoctest julia> T = tally([1, 1, 1, -1, -1, 2, 2, 3]) Tally with 8 items in 4 groups: 1  | 3 | 0.38% 2  | 2 | 0.25% -1 | 2 | 0.25% 3  | 1 | 0.12%

julia> T = tally([1, 1, 1, -1, -1, 2, 2, 3], by = abs) Tally with 8 items in 3 groups: [1] | 5 | 0.62% [2] | 2 | 0.25% [3] | 1 | 0.12%

julia> T = tally([1, 1, 1, -1, -1, 2, 2, 3], equivalence = (x, y) -> x^2 == y^2)

Tally with 8 items in 3 groups: [1] | 5 | 0.62% [2] | 2 | 0.25% [3] | 1 | 0.12%
