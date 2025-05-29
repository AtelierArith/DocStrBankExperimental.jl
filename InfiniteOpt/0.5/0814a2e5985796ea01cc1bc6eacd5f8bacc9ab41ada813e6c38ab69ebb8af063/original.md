```
parameter_refs(data::AbstractMeasureData)::Union{GeneralVariableRef,
                                                 AbstractArray{GeneralVariableRef}}
```

Return the infinite parameter reference(s) in `data`. This is intended as an internal function to be used with measure addition. User-defined measure data types will need to extend this function otherwise an error is thrown.
