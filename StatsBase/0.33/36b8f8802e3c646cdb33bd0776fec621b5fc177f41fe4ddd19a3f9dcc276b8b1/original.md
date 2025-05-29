```
winsor(x::AbstractVector; prop=0.0, count=0)
```

Return an iterator of all elements of `x` that replaces either `count` or proportion `prop` of the highest elements with the previous-highest element and an equal number of the lowest elements with the next-lowest element.

The number of replaced elements could be smaller than specified if several elements equal the lower or upper bound.

To compute the Winsorized mean of `x` use `mean(winsor(x))`.

# Example

```julia
julia> collect(winsor([5,2,3,4,1], prop=0.2))
5-element Array{Int64,1}:
 4
 2
 3
 4
 2
```
