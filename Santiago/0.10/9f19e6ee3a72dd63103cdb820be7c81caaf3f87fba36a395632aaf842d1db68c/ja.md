```julia
techs_per_template(
    systems::Array{Santiago.System}
) -> Dict{String, Set{String}}

```

各テンプレートのシステムによって使用されるすべての技術（ソースを含む）をリストします。
