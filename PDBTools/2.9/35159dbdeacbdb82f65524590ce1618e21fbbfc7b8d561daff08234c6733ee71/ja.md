```
add_protein_residue!(resname::String, reference_residue::PDBTools.ProteinResidue)
```

カスタムタンパク質残基をタンパク質残基のリストに追加するための関数です。この関数は追加された`ProteinResidue`オブジェクトを返します。すべてのカスタムタンパク質残基を削除するには`remove_custom_protein_residues!()`を使用します。

# 例

```jldoctest
julia> using PDBTools

julia> remove_custom_protein_residues!();

julia> add_protein_residue!("sA", PDBTools.protein_residues["ALA"])
PDBTools.ProteinResidue("sA", "ALA", "A", "Aliphatic", false, true, 71.037114, 71.0779, 0, true)

julia> isprotein(Atom(resname="sA"))
true

julia> remove_custom_protein_residues!(); # クリーンアップ
```

ここでは、タンパク質残基のリストにカスタム残基がないことを保証するために、テストコードの適切な実行を確保するために`remove_custom_residues!()`を繰り返し呼び出しています。
