```
vol(::Type{FourthOrderTensor{3}})
vol(::Type{SymmetricFourthOrderTensor{3}})
```

Construct volumetric fourth order identity tensor. This is only available in 3D.

# Examples

```jldoctest
julia> x = rand(Mat{3,3});

julia> I_vol = vol(FourthOrderTensor{3});

julia> I_vol ⊡₂ x ≈ vol(x)
true

julia> vol(FourthOrderTensor{3}) + dev(FourthOrderTensor{3}) ≈ one(FourthOrderTensor{3})
true
```
