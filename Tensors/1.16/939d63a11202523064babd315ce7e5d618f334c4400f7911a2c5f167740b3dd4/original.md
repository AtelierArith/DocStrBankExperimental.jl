```
dot(::Vec, ::Vec)
dot(::Vec, ::SecondOrderTensor)
dot(::SecondOrderTensor, ::Vec)
dot(::SecondOrderTensor, ::SecondOrderTensor)
```

Computes the dot product (single contraction) between two tensors. The symbol `⋅`, written `\cdot`, is overloaded for single contraction.

# Examples

```jldoctest
julia> A = rand(Tensor{2, 2})
2×2 Tensor{2, 2, Float64, 4}:
 0.325977  0.218587
 0.549051  0.894245

julia> B = rand(Tensor{1, 2})
2-element Vec{2, Float64}:
 0.35311164439921205
 0.39425536741585077

julia> dot(A, B)
2-element Vec{2, Float64}:
 0.2012851406726999
 0.5464374094589712

julia> A ⋅ B
2-element Vec{2, Float64}:
 0.2012851406726999
 0.5464374094589712
```
