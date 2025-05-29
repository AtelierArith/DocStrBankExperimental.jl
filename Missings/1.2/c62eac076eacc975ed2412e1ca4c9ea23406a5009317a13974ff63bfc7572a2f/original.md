```
passmissing(f)
```

Return a function that returns `missing` if any of its positional arguments are `missing` (even if their number or type is not consistent with any of the methods defined for `f`) and otherwise applies `f` to these arguments.

`passmissing` does not support passing keyword arguments to the `f` function.

# Examples

```jldoctest
julia> passmissing(sqrt)(4)
2.0

julia> passmissing(sqrt)(missing)
missing

julia> passmissing(sqrt).([missing, 4])
2-element Array{Union{Missing, Float64},1}:
  missing
   2.0

julia> passmissing((x,y)->"$x $y")(1, 2)
"1 2"

julia> passmissing((x,y)->"$x $y")(missing)
missing
```
