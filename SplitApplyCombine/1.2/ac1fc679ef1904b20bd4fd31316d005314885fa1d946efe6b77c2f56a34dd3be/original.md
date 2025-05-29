```
groupunique(groups, values)
```

Collect the unique elements of `values` by the corresponding element of `groups`, returning a dictinary of sets.

# Example

```julia
julia> groupunique([true,false,true,false,true], [1,2,1,2,3])
2-element Dictionary{Bool,Indices{Int64}}
  true │ {1, 3}
 false │ {2}
```
