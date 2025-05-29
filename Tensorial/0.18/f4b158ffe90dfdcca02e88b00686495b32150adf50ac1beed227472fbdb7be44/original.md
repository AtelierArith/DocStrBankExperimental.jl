```
rotmat(θ::Vec{3}; sequence::Symbol)
```

Convert Euler angles to rotation matrix. Use 3 characters belonging to the set (X, Y, Z) for intrinsic rotations, or (x, y, z) for extrinsic rotations.

# Examples

```jldoctest
julia> α, β, γ = map(deg2rad, rand(3));

julia> rotmat(Vec(α,β,γ), sequence = :XYZ) ≈ rotmatx(α) * rotmaty(β) * rotmatz(γ)
true

julia> rotmat(Vec(α,β,γ), sequence = :xyz) ≈ rotmatz(γ) * rotmaty(β) * rotmatx(α)
true

julia> rotmat(Vec(α,β,γ), sequence = :XYZ) ≈ rotmat(Vec(γ,β,α), sequence = :zyx)
true
```
