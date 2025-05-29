```julia
CreateUnitCell!(uc::UnitCell, param::Param , index::Int64=length(param.value))
CreateUnitCell!(uc::UnitCell, params::Vector{Param}, indices::Vector{Int64}=length.(getproperty.(params, :value)))
```

Add bonds corrsponding to a `param` to `UnitCell`, scaled with the `param.value[index]`. Also includes the broadcasted call.
