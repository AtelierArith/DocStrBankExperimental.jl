```
@𝔼(expr::JuMP.AbstractJuMPScalar,
   prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef};
   [num_supports::Int = DefaultNumSupports],
   kwargs...)::GeneralVariableRef
```

[`@expect`](@ref) の便利なラッパーです。ユニコードシンボル `𝔼` は `\bbE` によって生成されます。
