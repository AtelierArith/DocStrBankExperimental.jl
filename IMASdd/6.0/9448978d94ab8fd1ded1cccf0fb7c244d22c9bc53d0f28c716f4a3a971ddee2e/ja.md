```
@findall ids :symbol
@findall ids r"正規表現"
@findall [ids1, ids2] [:sybmol1, :symbol2]
@findall [ids1, ids2] r"正規表現"

指定されたフィールドを単一または複数のIDSオブジェクト内で検索し、それらの名前をIDS*Field*Finder.root_nameにキャプチャします。

このマクロが展開後に呼び出す[`findall(root_ids::Union{IDS,IDSvector}, target::Union{Symbol,AbstractArray{Symbol},Regex}=r""; kwargs)`](@ref)も参照してください。

# 引数

  * `root_ids:: 検索するルートIDSオブジェクト。
  * `target_fields::Union{Symbol, AbstractArray{Symbol}, Regex}: 単一のシンボル、シンボルの配列、または正規表現で指定された検索対象のフィールド。

# 戻り値

  * `Vector{IDS_Field_Finder}`: 各フィールドの詳細（親IDS、ルートIDS、フィールドタイプ、完全なフィールドパスを含む）を含む`IDS_Field_Finder`構造体のベクター。

# 例

```

julia-repl julia> @findall [dd1, dd2] [:psi, :j_tor] julia> @findall [dd1, dd2] r"psi"

julia> eqt = dd.equilibrium.time_slice[]

julia> @findall eqt :psi julia> @findall eqt r"global.*psi" ```
