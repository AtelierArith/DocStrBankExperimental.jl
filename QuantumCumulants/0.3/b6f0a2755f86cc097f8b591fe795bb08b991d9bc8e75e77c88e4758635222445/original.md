```
reorder(param,indexMapping)
```

Reorders a given term (param) regarding to a given indexMapping, which specifies, which [`Index`](@ref) entities can not be equal inside the given term. reorder() creates a [`SpecialIndexedTerm`](@ref) as a result.

# Examples

```
reorder(σⱼ²¹ * σᵢ²¹,[(i,j)]) = σᵢ²¹ * σⱼ²¹

reorder(σⱼ²¹ * σᵢ²¹ * σⱼ¹²,[(i,j)]) = σᵢ²¹ * σⱼ²²
```
