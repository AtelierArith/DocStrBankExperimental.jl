```
map_from_func(image_fn::Function, domain, codomain)
```

Construct the generic functional map with domain and codomain given by the parent objects $R$ and $S$ corresponding to the Julia function $f$.

# Examples

```jldoctest
julia> f = map_from_func(x -> x + 1, ZZ, ZZ)
Map defined by a Julia function
  from integers
  to integers

julia> f(ZZ(2))
3
```
