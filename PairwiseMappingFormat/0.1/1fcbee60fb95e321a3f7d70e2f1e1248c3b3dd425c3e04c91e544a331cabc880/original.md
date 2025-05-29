```
aux_data(rec::Record) -> XAMAuxData.SAM.Auxiliary
```

Return a lazily evaluated and validated `SAM.Auxiliary`, which is an `AbstractDict` of the auxiliary fields at the end of the record. For more details about this object, read the documentation of the package XAMAuxData.jl.

# Examples

```jldoctest
julia> aux = aux_data(record);

julia> length(aux)
4

julia> aux["cm"]
29990

julia> aux["k1"] = "add a new aux string like this";

julia> haskey(aux, "k1")
true
```
