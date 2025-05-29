```
stoichiometry(atoms::AbstractVector{<:Atom})
```

選択した原子の化学量論を `Formula` 構造体で返します。

### 例

```jldoctest
julia> using PDBTools

julia> pdb  = read_pdb(PDBTools.TESTPDB, "water"); # テスト用PDBファイル

julia> stoichiometry(pdb)
H₂O₁
```
