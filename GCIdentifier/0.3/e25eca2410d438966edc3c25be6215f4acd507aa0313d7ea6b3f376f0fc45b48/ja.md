```
get_groups_from_smiles(smiles::String,groups;connectivity = false,check = true)
```

SMILES文字列とグループリスト（`groups::Vector{GCPair}`）を与えると、グループのリストとそれに対応する数を返します。

`connectivity`がtrueの場合、各ペア間の結合の数を含むベクトルも追加で返します。

## 例

```julia
julia> get_groups_from_smiles("CCO",UNIFACGroups)
("CCO", ["CH3" => 1, "CH2" => 1, "OH(P)" => 1])

julia> get_groups_from_smiles("CCO",JobackGroups,connectivity = true)
("CCO", ["-CH3" => 1, "-CH2-" => 1, "-OH (alcohol)" => 1], [("-CH3", "-CH2-") => 1, ("-CH2-", "-OH (alcohol)") => 1])
```
