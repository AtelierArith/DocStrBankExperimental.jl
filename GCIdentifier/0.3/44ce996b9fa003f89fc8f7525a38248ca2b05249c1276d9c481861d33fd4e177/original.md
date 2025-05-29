```
find_missing_groups_from_smiles(smiles::String, groups;max_group_size = nothing, environment=false, reduced=false)
```

Given a SMILES string and a group list (`groups::Vector{GCPair}`), returns a list of potential groups (`new_groups::Vector{GCPair}`) which could cover those atoms not covered within `groups`. If no `groups` vector is provided, it will simply generate all possible groups for the molecule.

A set of heuristics are built into the code when it comes to combining heavy atoms into large groups:

1. If a carbon atom is bonded to another carbon atom, unless only one of the carbons is on a ring, they will not be combined into a group.
2. All other combinations of atoms are allowed.

The logic behind the first heuristic is due to the fact that neighbouring atoms with similar electronegativities won't have a great impact on each other's properties. As such, they are not combined into a group. In the future, this approach could be extended to use HNMR data to determine which atoms can be combined into the same group.

Optional arguments:

  * `max_group_size::Int`: The maximum number of atoms within a group to be generated. If `nothing`, the maximum size is however many atoms a central atom is bonded to.
  * `environment::Bool`: If true, the groups SMARTS will include information about the environment of the group is in. For example, in pentane, if environment is false, there will only be one CH2 group, whereas, if environment is true, there will be two CH2 groups, one bonded to CH3 and one bonded to another CH2.
  * `reduced::Bool`: If true, the groups will be generated such that the minimum number of groups required to represent the molecule, based on `max_group_size`, will be generated. If false, all possible groups will be generated.

## Example

```julia
julia> find_missing_groups_from_smiles("CC(=O)O")
7-element Vector{GCIdentifier.GCPair}:
 GCIdentifier.GCPair("[CX4;H3;!R]", "CH3")
 GCIdentifier.GCPair("[CX3;H0;!R]", "C=")
 GCIdentifier.GCPair("[OX1;H0;!R]", "O=")
 GCIdentifier.GCPair("[OX2;H1;!R]", "OH")
 GCIdentifier.GCPair("[CX3;H0;!R](=[OX1;H0;!R])", "C=O=")
 GCIdentifier.GCPair("[CX3;H0;!R]([OX2;H1;!R])", "C=OH")
 GCIdentifier.GCPair("[CX3;H0;!R](=[OX1;H0;!R])([OX2;H1;!R])", "C=O=OH")
```
