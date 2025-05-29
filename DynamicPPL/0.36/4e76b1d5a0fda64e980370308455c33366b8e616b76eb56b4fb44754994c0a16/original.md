```
subset(vnv::VarNamedVector, vns::AbstractVector{<:VarName})
```

Return a new `VarNamedVector` containing the values from `vnv` for variables in `vns`.

Which variables to include is determined by the `VarName`'s `subsumes` relation, meaning that e.g. `subset(vnv, [@varname(x)])` will include variables like `@varname(x.a[1])`.

Preserves the order of variables in `vnv`.

# Examples

```jldoctest varnamedvector-subset julia> using DynamicPPL: VarNamedVector, @varname, subset

julia> vnv = VarNamedVector(@varname(x) => [1.0, 2.0], @varname(y) => [3.0]);

julia> subset(vnv, [@varname(x)]) == VarNamedVector(@varname(x) => [1.0, 2.0]) true

julia> subset(vnv, [@varname(x[2])]) == VarNamedVector(@varname(x[2]) => [2.0]) true
