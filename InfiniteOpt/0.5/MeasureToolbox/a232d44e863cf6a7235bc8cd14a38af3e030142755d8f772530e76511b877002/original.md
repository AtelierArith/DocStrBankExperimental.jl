```
@𝔼(expr::JuMP.AbstractJuMPScalar,
   prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef};
   [num_supports::Int = DefaultNumSupports],
   kwargs...)::GeneralVariableRef
```

A convenient wrapper for [`@expect`](@ref). The unicode symbol `𝔼` is produced by  `\bbE`.
