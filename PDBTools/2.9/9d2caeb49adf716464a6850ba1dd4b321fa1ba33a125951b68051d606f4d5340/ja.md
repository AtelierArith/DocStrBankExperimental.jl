```
add_element!(symbol::String, reference_element::PDBTools.Element; elements=PDBTools.elements)
```

要素辞書に新しい要素を追加します。要素がすでに存在する場合は上書きされます。

すべてのカスタム要素を削除するには、`remove_custom_elements!()`を使用します。

# 例

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> using PDBTools

julia> remove_custom_elements!(); # もしあれば

julia> atoms = [ Atom(name="A1"), Atom(name="A2") ];

julia> add_element!("A1", PDBTools.elements["C"])
PDBTools.Element(:C, "C", "Carbon", 6, 12.011, true)

julia> add_element!("A2", PDBTools.elements["N"])
PDBTools.Element(:N, "N", "Nitrogen", 7, 14.0067, true)

julia> element(atoms[1])
"C"

julia> element(atoms[2])
"N"

julia> mass(atoms)
26.017699999999998

julia> remove_custom_elements!(); 
```

ここでは、テストコードが適切に実行されることを保証するために、カスタム要素が事前に定義されていない状態で`remove_custom_elements!()`を繰り返し呼び出しています。
