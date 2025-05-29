```
dev(::Type{FourthOrderTensor{3}})
dev(::Type{SymmetricFourthOrderTensor{3}})
```

Construct deviatoric fourth order identity tensor. This is only available in 3D.

# Examples

```jldoctest
julia> x = rand(Mat{3,3});

julia> I_dev = dev(FourthOrderTensor{3});

julia> I_dev ⊡₂ x ≈ dev(x)
true

julia> vol(FourthOrderTensor{3}) + dev(FourthOrderTensor{3}) ≈ one(FourthOrderTensor{3})
true
```
