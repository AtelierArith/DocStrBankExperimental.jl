```
physical_realify(irs::Collection{T}) where T <: Union{<:PGIrrep, <:SiteIrrep}
```

Return a manifestly real form of `irs` (also known as physically real irreps), where `irs` is a [`Collection`](@ref) of either [`PGIrrep`](@ref)s or [`SiteIrrep`](@ref)s.

The input irreps may or may not have already been passed through [`realify`](@ref) (and thus already glued together with any pseudoreal or complex partners); if they have not, the input is first passed through `realify`.

See also [`physical_realify(::Union{<:PGIrrep, <:SiteIrrep})`](@ref) for application to individual irreps.

## Examples

```jldoctest
julia> pgirs = pgirreps(9,2);

julia> physical_realify(pgirs)
4-element Collection{PGIrrep{2}} for ⋕9 (6):
Γ₁┌  1: 1
  ├ 3⁺: 1
  ├ 3⁻: 1
  ├  2: 1
  ├ 6⁻: 1
  └ 6⁺: 1

Γ₂┌  1: 1
  ├ 3⁺: 1
  ├ 3⁻: 1
  ├  2: -1
  ├ 6⁻: -1
  └ 6⁺: -1

Γ₃Γ₅┌  1: ⎡ 1  0 ⎤
    │     ⎣ 0  1 ⎦
    ├ 3⁺: ⎡   -0.5  0.866 ⎤
    │     ⎣ -0.866   -0.5 ⎦
    ├ 3⁻: ⎡  -0.5  -0.866 ⎤
    │     ⎣ 0.866    -0.5 ⎦
    ├  2: ⎡ 1  0 ⎤
    │     ⎣ 0  1 ⎦
    ├ 6⁻: ⎡   -0.5  0.866 ⎤
    │     ⎣ -0.866   -0.5 ⎦
    ├ 6⁺: ⎡  -0.5  -0.866 ⎤
    └     ⎣ 0.866    -0.5 ⎦

Γ₄Γ₆┌  1: ⎡ 1  0 ⎤
    │     ⎣ 0  1 ⎦
    ├ 3⁺: ⎡   -0.5  0.866 ⎤
    │     ⎣ -0.866   -0.5 ⎦
    ├ 3⁻: ⎡  -0.5  -0.866 ⎤
    │     ⎣ 0.866    -0.5 ⎦
    ├  2: ⎡ -1   0 ⎤
    │     ⎣  0  -1 ⎦
    ├ 6⁻: ⎡   0.5  -0.866 ⎤
    │     ⎣ 0.866     0.5 ⎦
    ├ 6⁺: ⎡    0.5  0.866 ⎤
    └     ⎣ -0.866    0.5 ⎦
```
