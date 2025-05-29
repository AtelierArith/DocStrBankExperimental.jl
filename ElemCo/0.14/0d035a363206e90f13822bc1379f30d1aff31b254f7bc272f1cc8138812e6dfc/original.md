```
@ECinit()
```

Initialize `EC::ECInfo` and add molecular system and/or fcidump    if variables `geometry::String` and `basis::Dict{String,Any}`   and/or `fcidump::String` are defined.

If `EC` is already initialized, it will be overwritten.

# Examples

```julia
geometry="He 0.0 0.0 0.0"
basis = Dict("ao"=>"cc-pVDZ", "jkfit"=>"cc-pvtz-jkfit", "mpfit"=>"cc-pvdz-mpfit")
@ECinit
# output
Occupied orbitals:[1]

```
