```
physical_realify(ir::Union{<:PGIrrep, <:SiteIrrep})
```

Return a manifestly real form of an input irrep `ir` (also called a physically real irrep).

The input irrep must be either a [`PGIrrep`](@ref) or a [`SiteIrrep`](@ref) and must be equivalent to a real irrep: i.e., the irrep has [`Reality`](@ref) type `REAL` or is a `PSEUDOREAL` or `COMPLEX` that has already been passed through `realify` and glued together with its partner (i.e., `iscorep(ir) = true`).

See also [`physical_realify(::Collection{<:Union{<:PGIrrep, <:SiteIrrep}})`](@ref) for application to a collection of irreps.

## Implementation

A symmetric, unitary transformation is found that maps the irrep matrices to a manifestly real form. The resulting transformed irrep matrices `Zs` have the property that `all(Zᵢ -> Zᵢ ≈ conj(Zᵢ), Zs)` is true.

## Examples

```jldoctest
julia> pgir = pgirreps(19, 3)[end]
Γ₃┌     1: ⎡ 1  0 ⎤
  │        ⎣ 0  1 ⎦
  ├ 3₀₀₁⁺: ⎡ -0.5+0.866im             0 ⎤
  │        ⎣            0  -0.5-0.866im ⎦
  ├ 3₀₀₁⁻: ⎡ -0.5-0.866im             0 ⎤
  │        ⎣            0  -0.5+0.866im ⎦
  ├  m₁₁₀: ⎡ 0  1 ⎤
  │        ⎣ 1  0 ⎦
  ├  m₁₀₀: ⎡            0  -0.5-0.866im ⎤
  │        ⎣ -0.5+0.866im             0 ⎦
  ├  m₀₁₀: ⎡            0  -0.5+0.866im ⎤
  └        ⎣ -0.5-0.866im             0 ⎦

julia> reality(pgir)
REAL::Reality = 1

julia> physical_realify(pgir)
Γ₃┌     1: ⎡ 1  0 ⎤
  │        ⎣ 0  1 ⎦
  ├ 3₀₀₁⁺: ⎡   -0.5  0.866 ⎤
  │        ⎣ -0.866   -0.5 ⎦
  ├ 3₀₀₁⁻: ⎡  -0.5  -0.866 ⎤
  │        ⎣ 0.866    -0.5 ⎦
  ├  m₁₁₀: ⎡ 0  1 ⎤
  │        ⎣ 1  0 ⎦
  ├  m₁₀₀: ⎡ -0.866   -0.5 ⎤
  │        ⎣   -0.5  0.866 ⎦
  ├  m₀₁₀: ⎡ 0.866    -0.5 ⎤
  └        ⎣  -0.5  -0.866 ⎦
```
