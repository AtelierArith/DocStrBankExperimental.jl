```
group(groups, values)
```

Return a dictionary of the elements of `values` grouped by the label inidcated by by the matching element from `groups`.

# Example

```julia
julia> group([true,false,true,false,true], [1,2,3,4,5])
2-element Dictionary{Bool,Array{Int64,1}}
  true │ [1, 3, 5]
 false │ [2, 4]
```
