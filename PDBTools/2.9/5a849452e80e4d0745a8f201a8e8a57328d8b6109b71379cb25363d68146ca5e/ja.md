```
残基
```

残基データ構造。

残基構造は、含まれる原子の残基または分子の特性を持っていますが、元の原子ベクトルをコピーすることはなく、各残基の残基メタデータのみを保持します。したがって、残基の原子に対する変更は、元の原子ベクトルに反映されます。

### 例

```jldoctest
julia> using PDBTools

julia> pdb = wget("1LBD");

julia> residues = collect(eachresidue(pdb))
238-element Vector{Residue}[
    SER225A
    ALA226A
    ⋮
    MET461A
    THR462A
]

julia> resnum.(residues[1:3])
3-element Vector{Int32}:
 225
 226
 227

julia> residues[5].chain
"A"

julia> residues[8].range
52:58

julia> mass(residues[1])
82.0385

```
