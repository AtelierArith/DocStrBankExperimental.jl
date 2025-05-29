```
Base.setproperty!(@nospecialize(ids::IDS), field::Symbol, value::AbstractArray{<:IDS}; skip_non_coordinates::Bool=false, error_on_missing_coordinates::Bool=true)
```

Handle setproperty of entire vectors of IDS structures at once (ids.field is of type IDSvector)
