```
show_variables(domain::Domain; [attributes], [filter], showlinks=false, modeldata=nothing) -> DataFrame
```

Show table of Domain Variables. Optionally get variable links, data.

# Keywords:

  * `attributes=[:units, :vfunction, :space, :field_data, :description]`: Variable attributes to show
  * `showlinks=false`: true to show [`VariableReaction`](@ref)s that link to this Domain Variable.
  * `modeldata=nothing`: set to also show Variable values.
  * `filter=attrb->true`: function to filter by Variable attributes. Example: `filter=attrb->attrb[:vfunction]!=PB.VF_Undefined` to show state Variables and derivatives.
