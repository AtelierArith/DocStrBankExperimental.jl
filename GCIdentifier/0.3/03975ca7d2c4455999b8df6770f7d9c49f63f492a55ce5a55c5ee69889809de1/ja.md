```
get_groups_from_name(name::String,groups;connectivity = false)
```

分子名とグループリスト（`groups::Vector{GCPair}`）を指定すると、グループのリストとそれに対応する数を返します。

`connectivity`が`true`の場合、各ペア間の結合の数を含むベクトルも追加で返します。

注意: ChemicalIdentifiersパッケージがインストールされ、ロードされている場合にのみ使用できます（`using ChemicalIdentifiers`）。

## 例

```julia
julia> get_groups_from_name("ethanol",UNIFACGroups)
("ethanol", ["CH3" => 1, "CH2" => 1, "OH(P)" => 1])

julia> get_groups_from_name("ethanol",JobackGroups,connectivity = true)
("ethanol", ["-CH3" => 1, "-CH2-" => 1, "-OH (alcohol)" => 1], [("-CH3", "-CH2-") => 1, ("-CH2-", "-OH (alcohol)") => 1])
```
