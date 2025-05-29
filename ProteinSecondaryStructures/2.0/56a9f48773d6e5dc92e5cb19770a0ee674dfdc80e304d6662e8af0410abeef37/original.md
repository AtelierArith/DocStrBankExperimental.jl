```
ss_name(ss::Union{SSData, Integer, String, Char})
```

Return the secondary structure name. The input may be a `SSData` object,  a secondary structure `Integer` code (1-10) or a secondary  structure code (`G, H, ..., C`).

The classification follows the DSSP standard classes, described  in the ProteinSecondaryStructures.jl documentation.

## Example

```jldoctest
julia> using ProteinSecondaryStructures

julia> ss_name("H")
"alpha helix"

julia> ss_name(1)
"310 helix"

julia> ss = SSData("ARG", "A", 1, "H", 0.0, 0.0)
SSData("ARG", "A", 1, "H", 0.0, 0.0)

julia> ss_name(ss)
"alpha helix"
```
