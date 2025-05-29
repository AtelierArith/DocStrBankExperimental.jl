```
residue_ticks(
    atoms (または) residues (または) residue iterator; 
    first=nothing, last=nothing, stride=1, oneletter=true, serial=false
)
```

与えられた原子に対して、プロットの目盛りラベルとして使用するための残基番号と残基名のタプルを返します。

構造データは、`Atom`のベクター、`Residue`のベクター、または`eachresidue`イテレータを提供できます。

`first`と`last`は、含める残基番号を参照する整数のオプションのキーワードパラメータです。`stride`オプションを使用して、残基をスキップし、目盛りラベルを整理できます。

`oneletter`が`false`の場合、三文字の残基コードが返されます。名前が不明な残基は`X`または`XXX`と名付けられます。

`serial=true`の場合、連続した残基インデックスが目盛りのインデックスとして使用されます。代わりに`serial=false`の場合、位置は残基番号に設定されます。

# 例

```jldoctest
julia> using PDBTools

julia> atoms = wget("1LBD", "protein");

julia> residue_ticks(atoms; stride=50) # 入力としてのVector{<:Atom}
(Int32[225, 275, 325, 375, 425], ["S225", "Q275", "L325", "L375", "L425"])

julia> residue_ticks(atoms; first=235, last=240) # first=10
(Int32[235, 236, 237, 238, 239, 240], ["I235", "L236", "E237", "A238", "E239", "L240"])

julia> residue_ticks(eachresidue(atoms); stride=50) # 入力としての残基イテレータ
(Int32[225, 275, 325, 375, 425], ["S225", "Q275", "L325", "L375", "L425"])

julia> residue_ticks(collect(eachresidue(atoms)); stride=50) # 入力としてのVector{Residue}
(Int32[225, 275, 325, 375, 425], ["S225", "Q275", "L325", "L375", "L425"])

julia> residue_ticks(atoms; first=10, stride=50, serial=true) # serial=trueを使用
(10:50:210, ["R234", "K284", "R334", "S384", "E434"])

```

得られた残基番号とラベルのタプルは、例えば`Plots.plot`の`xticks`として使用できます。
