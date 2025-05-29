```
remove_custom_elements!()
```

要素辞書からすべてのカスタム要素を削除します。

# 例

```jldoctest
julia> using PDBTools

julia> remove_custom_elements!();

julia> add_element!("GN", PDBTools.elements["N"])
PDBTools.Element(:N, "N", "Nitrogen", 7, 14.0067, true)

julia> element(Atom(name="GN"))
"N"

julia> remove_custom_elements!();

julia> element(Atom(name="GN")) # `nothing`を返します

```

ここでは、カスタム要素が事前に定義されていないことを保証するために、テストコードの適切な実行を確保するために`remove_custom_elements!()`を繰り返し呼び出します。
