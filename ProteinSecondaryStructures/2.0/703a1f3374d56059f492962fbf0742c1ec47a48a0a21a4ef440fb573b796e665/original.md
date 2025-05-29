```
ss_number(code::Union{SSData,AbstractString,AbstractChar})
```

Returns the secondary structure number code. The input may be a secondary structure `String` code, a secondary structure name (`"310 helix"`, `"alpha helix"`, ..., `"coil"`), or a `SSData` object.

The classification follows the DSSP standard classes, described  in the ProteinSecondaryStructures.jl documentation.

# Example

```jldoctest
julia> using ProteinSecondaryStructures

julia> ss_number("H")
2

julia> ss_number('B')
7

julia> ss_number("beta bridge")
7

julia> ss = SSData("ARG", "A", 1, "H", 0.0, 0.0)
SSData("ARG", "A", 1, "H", 0.0, 0.0)

julia> ss_number(ss)
2

```
