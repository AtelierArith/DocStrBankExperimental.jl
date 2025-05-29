```
Tensor{order,dim,T<:Number}
```

`order ∈ (1,2,4)` および `dim ∈ (1,2,3)` に対してサポートされているテンソル型です。

# 例

```jldoctest
julia> Tensor{1,3,Float64}((1.0, 2.0, 3.0))
3-element Vec{3, Float64}:
 1.0
 2.0
 3.0
```
