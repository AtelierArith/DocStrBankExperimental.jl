```
eachresidue(atoms::AbstractVector{<:Atom})
```

選択の残基（または分子）のイテレータ。

### 例

```jldoctest
julia> using PDBTools

julia> atoms = wget("1LBD");

julia> eachresidue(atoms)
 残基イテレータの長さ = 238

julia> collect(eachresidue(atoms))
238要素のベクトル{Residue}[
    SER225A
    ALA226A
    ⋮
    MET461A
    THR462A
]
```
