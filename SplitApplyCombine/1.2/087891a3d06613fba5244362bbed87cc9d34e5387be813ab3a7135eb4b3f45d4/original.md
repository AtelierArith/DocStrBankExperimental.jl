```
groupfind([by], container)
```

Seperate the indices `i` of `container` into groups labeled by `by(container[i])`, where the default value of `by` is `identity`.

# Example

```jldoctest
julia> groupfind(iseven, [3,4,2,6,5,8])
2-element Dictionary{Bool,Array{Int64,1}}
 false │ [1, 5]
  true │ [2, 3, 4, 6]
```
