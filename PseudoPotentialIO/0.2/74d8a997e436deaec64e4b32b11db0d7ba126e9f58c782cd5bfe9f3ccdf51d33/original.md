```julia
show_family_list(
    family_name_or_dir::AbstractString;
    elements
) -> Dict

```

List the pseudopotentials in a pseudopotential family in a pretty table. The elements for which pseudos are shown can be restricted by passing a list of strings, e.g. ["Ag"].

```julia
show_family_list(family_name_or_dir; elements)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/load.jl:95`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/load.jl).
