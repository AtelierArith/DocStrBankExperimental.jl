```
vol(::Type{FourthOrderTensor{3}})
vol(::Type{SymmetricFourthOrderTensor{3}})
```

体積の四次単位テンソルを構築します。これは3Dでのみ利用可能です。

# 例

```jldoctest
julia> x = rand(Mat{3,3});

julia> I_vol = vol(FourthOrderTensor{3});

julia> I_vol ⊡₂ x ≈ vol(x)
true

julia> vol(FourthOrderTensor{3}) + dev(FourthOrderTensor{3}) ≈ one(FourthOrderTensor{3})
true
```
