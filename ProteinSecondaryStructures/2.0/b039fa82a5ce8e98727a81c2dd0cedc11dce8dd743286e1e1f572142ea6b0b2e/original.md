```
ss_code(code::Union{SSData,String,Integer})
```

Returns the one-letter secondary structure code. The input may be a secondary structure `Integer` code, a secondary structure name (`"310 helix"`, `"alpha helix"`, ..., `"coil"`), or a `SSData` object.

The classification follows the DSSP standard classes, described  in the ProteinSecondaryStructures.jl documentation.

# Example

```jldoctest
julia> using ProteinSecondaryStructures

julia> ss_code(2)
"H"

julia> ss_code("beta bridge")
"B"

julia> ss = SSData("ARG", "A", 1, "H", 0.0, 0.0)
SSData("ARG", "A", 1, "H", 0.0, 0.0)

julia> ss_code(ss)
"H"

```
