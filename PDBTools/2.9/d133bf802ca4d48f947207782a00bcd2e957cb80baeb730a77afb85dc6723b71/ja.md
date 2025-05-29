```
remove_custom_protein_residues!()
```

すべてのカスタムタンパク質残基をタンパク質残基のリストから削除する関数です。

# 例

```jldoctest
julia> using PDBTools

julia> remove_custom_protein_residues!(); # クリーンアップ

julia> add_protein_residue!("sA", PDBTools.protein_residues["ALA"])
PDBTools.ProteinResidue("sA", "ALA", "A", "Aliphatic", false, true, 71.037114, 71.0779, 0, true)

julia> isprotein(Atom(resname="sA"))
true

julia> remove_custom_protein_residues!();

julia> isprotein(Atom(resname="sA"))
false
```

ここでは、タンパク質残基のリストにカスタム残基がないことを保証するために、`remove_custom_residues!()`を繰り返し呼び出してテストコードの適切な実行を確認しています。
