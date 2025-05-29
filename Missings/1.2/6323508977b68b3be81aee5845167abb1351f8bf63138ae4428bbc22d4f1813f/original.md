```
missingsmallest(x, y)
```

The standard partial order `isless` modified so that `missing` is always the smallest possible value:

  * If neither argument is `missing`, the function behaves exactly as `isless`.
  * If `y` is `missing` the result will be `false` regardless of the value of `x`.
  * If `x` is `missing` the result will be `true` unless `y` is `missing`.

See also the 1-argument method which takes a partial ordering function (like `isless`) and modifies it to treat `missing` as explained above. These functions can be used together with sorting functions so that missing values are sorted first. This is useful in particular so that when sorting in reverse order missing values appear at the end.

# Examples

```jldoctest julia> sort(v, lt=missingsmallest) 5-element Vector{Union{Missing, Int64}}:    missing    missing   1   2  10

julia> sort(v, lt=missingsmallest, rev=true) 5-element Vector{Union{Missing, Int64}}:  10   2   1    missing    missing

julia> missingsmallest(missing, Inf) true

julia> missingsmallest(-Inf, missing) false

julia> missingsmallest(missing, missing) false
