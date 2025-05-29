```
eachchain(atoms::AbstractVector{<:Atom})
```

選択のチェーンのためのイテレータ。

### 例

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.CHAINSPDB);

julia> eachchain(ats)
 チェーンイテレータの長さ = 4

julia> chains = collect(eachchain(ats))
4要素のベクター{Chain}[
    Chain(A-48 atoms)
    Chain(B-48 atoms)
    Chain(A-48 atoms)
    Chain(D-45 atoms)
]
```
