```
physical_realify(ir::Union{<:PGIrrep, <:SiteIrrep})
```

入力の irrep `ir`（物理的に実な irrep とも呼ばれる）の明示的な実形式を返します。

入力の irrep は [`PGIrrep`](@ref) または [`SiteIrrep`](@ref) のいずれかでなければならず、実な irrep と同等である必要があります。すなわち、irrep の [`Reality`](@ref) 型が `REAL` であるか、`PSEUDOREAL` または `COMPLEX` であり、すでに `realify` を通過し、そのパートナーと一緒に接着されている必要があります（すなわち、`iscorep(ir) = true`）。

irreps のコレクションに適用するための [`physical_realify(::Collection{<:Union{<:PGIrrep, <:SiteIrrep}})`](@ref) も参照してください。

## 実装

irrep 行列を明示的な実形式にマッピングする対称的なユニタリ変換が見つかります。結果として得られる変換された irrep 行列 `Zs` は、`all(Zᵢ -> Zᵢ ≈ conj(Zᵢ), Zs)` が真であるという特性を持ちます。

## 例

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
