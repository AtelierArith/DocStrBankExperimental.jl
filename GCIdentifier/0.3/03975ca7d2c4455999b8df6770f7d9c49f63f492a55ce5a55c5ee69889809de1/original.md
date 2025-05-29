```
get_groups_from_name(name::String,groups;connectivity = false)
```

Given a molecule name and a group list (`groups::Vector{GCPair}`), returns a list of groups and their corresponding amount.

If `connectivity` is `true`, then it will additionally return a vector containing the amount of bonds between each pair.

Note: Can only be used if the ChemicalIdentifiers package is also installed and loaded (`using ChemicalIdentifiers`).

## Examples

```julia
julia> get_groups_from_name("ethanol",UNIFACGroups)
("ethanol", ["CH3" => 1, "CH2" => 1, "OH(P)" => 1])

julia> get_groups_from_name("ethanol",JobackGroups,connectivity = true)
("ethanol", ["-CH3" => 1, "-CH2-" => 1, "-OH (alcohol)" => 1], [("-CH3", "-CH2-") => 1, ("-CH2-", "-OH (alcohol)") => 1])
```
