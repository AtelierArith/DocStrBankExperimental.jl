```
get_array(output::PALEOmodel.AbstractOutputWriter, varname::AbstractString [, allselectargs::NamedTuple]; kwargs...) -> FieldArray
[deprecated] get_array(output::PALEOmodel.AbstractOutputWriter, varname::AbstractString; allselectargs...) -> FieldArray
```

Return a [`PALEOmodel.FieldArray`](@ref) containing data values and any attached coordinates.

Equivalent to `PALEOmodel.get_array(PB.get_field(output, varname), allselectargs; kwargs)`, see [`PALEOmodel.get_array(fr::PALEOmodel.FieldRecord)`](@ref).
