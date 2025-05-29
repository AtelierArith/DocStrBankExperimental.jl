```
GroupParam
```

Struct holding group parameters.contains:

  * `components`: a list of all components
  * `groups`: a list of groups names for each component
  * `grouptype`: used to differenciate between different group models.
  * `i_groups`: a list containing the number of groups for each component
  * `n_groups`: a list of the group multiplicity of each group corresponding to each group in `i_groups`
  * `n_intragroups`: a list containining the connectivity graph (as a matrix) between each group for each component.
  * `flattenedgroups`: a list of all unique groups–the parameters correspond to this list
  * `n_flattenedgroups`: the group multiplicities corresponding to each group in `flattenedgroups`

You can create a group param by passing a `Vector{Tuple{String, Vector{Pair{String, Int64}}}}. For example:

```julia-repl
julia> grouplist = [
           ("ethanol", ["CH3"=>1, "CH2"=>1, "OH"=>1]),
           ("nonadecanol", ["CH3"=>1, "CH2"=>18, "OH"=>1]),
           ("ibuprofen", ["CH3"=>3, "COOH"=>1, "aCCH"=>1, "aCCH2"=>1, "aCH"=>4])];
julia> groups = GroupParam(grouplist)
GroupParam(:unknown) with 3 components:
 "ethanol": "CH3" => 1, "CH2" => 1, "OH" => 1
 "nonadecanol": "CH3" => 1, "CH2" => 18, "OH" => 1
 "ibuprofen": "CH3" => 3, "COOH" => 1, "aCCH" => 1, "aCCH2" => 1, "aCH" => 4
julia> groups.flattenedgroups
7-element Vector{String}:
 "CH3"
 "CH2"
 "OH"
 "COOH"
 "aCCH"
 "aCCH2"
 "aCH"
julia> groups.i_groups
3-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 2, 3]
 [1, 4, 5, 6, 7]
julia> groups.n_groups
3-element Vector{Vector{Int64}}:
 [1, 1, 1]
 [1, 18, 1]
 [3, 1, 1, 1, 4]
julia> groups.n_flattenedgroups
 3-element Vector{Vector{Int64}}:
 [1, 1, 1, 0, 0, 0, 0]
 [1, 18, 1, 0, 0, 0, 0]
 [3, 0, 0, 1, 1, 1, 4]
```

if you have CSV with group data, you can also pass those, to automatically query the missing groups in your input vector:

```julia-repl
julia> grouplist = [
           "ethanol",
           ("nonadecanol", ["CH3"=>1, "CH2"=>18, "OH"=>1]),
           ("ibuprofen", ["CH3"=>3, "COOH"=>1, "aCCH"=>1, "aCCH2"=>1, "aCH"=>4])];
           julia> groups = GroupParam(grouplist, ["SAFT/SAFTgammaMie/SAFTgammaMie_groups.csv"])
           GroupParam with 3 components:
            "ethanol": "CH2OH" => 1, "CH3" => 1
            "nonadecanol": "CH3" => 1, "CH2" => 18, "OH" => 1
            "ibuprofen": "CH3" => 3, "COOH" => 1, "aCCH" => 1, "aCCH2" => 1, "aCH" => 4
```

In this case, `SAFTGammaMie` files support the second order group `CH2OH`.
