```
get_array(output::PALEOmodel.AbstractOutputWriter, varname::AbstractString [, allselectargs::NamedTuple]; kwargs...) -> FieldArray
[deprecated] get_array(output::PALEOmodel.AbstractOutputWriter, varname::AbstractString; allselectargs...) -> FieldArray
```

データ値と添付された座標を含む [`PALEOmodel.FieldArray`](@ref) を返します。

`PALEOmodel.get_array(PB.get_field(output, varname), allselectargs; kwargs)` と同等であり、[`PALEOmodel.get_array(fr::PALEOmodel.FieldRecord)`](@ref) を参照してください。
