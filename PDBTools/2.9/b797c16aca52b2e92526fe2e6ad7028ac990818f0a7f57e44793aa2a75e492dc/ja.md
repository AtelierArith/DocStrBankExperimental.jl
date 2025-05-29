```
getseq(AbstractVector{<:Atom} or filename; selection, code)
```

アミノ酸の配列を原子のベクターまたはファイル名から返します。選択が適用される場合があります。コードは、出力が1文字、3文字、または完全な残基名の配列になるかを定義します。

### 例

```jldoctest
julia> using PDBTools

julia> protein = read_pdb(PDBTools.TESTPDB);

julia> getseq(protein,"residue < 3")
2-element Vector{String}:
 "A"
 "C"

julia> getseq(protein,"residue < 3", code=2)
2-element Vector{String}:
 "ALA"
 "CYS"

julia> getseq(protein,"residue < 3",code=3)
2-element Vector{String}:
 "Alanine"
 "Cysteine"

```
