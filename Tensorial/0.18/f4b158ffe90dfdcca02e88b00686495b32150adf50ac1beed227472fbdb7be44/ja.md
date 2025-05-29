```
rotmat(θ::Vec{3}; sequence::Symbol)
```

オイラー角を回転行列に変換します。内的回転には(X, Y, Z)のセットに属する3文字、外的回転には(x, y, z)のセットに属する3文字を使用してください。

# 例

```jldoctest
julia> α, β, γ = map(deg2rad, rand(3));

julia> rotmat(Vec(α,β,γ), sequence = :XYZ) ≈ rotmatx(α) * rotmaty(β) * rotmatz(γ)
true

julia> rotmat(Vec(α,β,γ), sequence = :xyz) ≈ rotmatz(γ) * rotmaty(β) * rotmatx(α)
true

julia> rotmat(Vec(α,β,γ), sequence = :XYZ) ≈ rotmat(Vec(γ,β,α), sequence = :zyx)
true
```
