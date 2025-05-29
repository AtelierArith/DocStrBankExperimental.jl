```
formula(atoms::AbstractVector{<:Atom})
```

現在の選択の分子式を返します。出力はインデックス可能な「Formula」構造体であり、各要素は元素名と原子の数を含むタプルです。

## 例

```jldoctest
julia> using PDBTools

julia> pdb  = read_pdb(PDBTools.TESTPDB, "residue 1"); # PDBファイルのテスト

julia> resname(pdb[1])
"ALA"

julia> f = formula(pdb)
H₇C₃N₁O₁

julia> f[1]
("H", 7)

```
