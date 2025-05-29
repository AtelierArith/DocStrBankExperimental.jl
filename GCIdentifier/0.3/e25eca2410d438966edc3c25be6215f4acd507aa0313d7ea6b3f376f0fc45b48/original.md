```
get_groups_from_smiles(smiles::String,groups;connectivity = false,check = true)
```

Given a SMILES string and a group list (`groups::Vector{GCPair}`), returns a list of groups and their corresponding amount.

If `connectivity` is true, then it will additionally return a vector containing the amount of bonds between each pair.

## Examples

```julia
julia> get_groups_from_smiles("CCO",UNIFACGroups)
("CCO", ["CH3" => 1, "CH2" => 1, "OH(P)" => 1])

julia> get_groups_from_smiles("CCO",JobackGroups,connectivity = true)
("CCO", ["-CH3" => 1, "-CH2-" => 1, "-OH (alcohol)" => 1], [("-CH3", "-CH2-") => 1, ("-CH2-", "-OH (alcohol)") => 1])
```
