```
group_replace(grouplist,keys...)
```

[`get_groups_from_smiles`](@ref) によって生成されたグループリストに対して、`grouplist` 内の特定のグループを `keys` で指定された値に置き換えます。

## 例

```
groups1 = get_groups_from_smiles("CCO", UNIFACGroups) #["CH3" => 1, "CH2" => 1, "OH(P)" => 1]
#各 "OH(P)" を 1 つの "OH" グループに置き換えます
#そして各 "CH3" グループを 3 つの "H" グループと 1 つの "C" グループに置き換えます
groups2 = group_replace(groups1[2],"OH(P)" => ("OH" => 1), "CH3" => [("C" => 1),("H" => 3)])
```
