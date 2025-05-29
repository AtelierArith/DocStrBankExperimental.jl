```
Tensor{order,dim,T<:Number}
```

Tensor type supported for `order ∈ (1,2,4)` and `dim ∈ (1,2,3)`.

# Examples

```jldoctest
julia> Tensor{1,3,Float64}((1.0, 2.0, 3.0))
3-element Vec{3, Float64}:
 1.0
 2.0
 3.0
```
