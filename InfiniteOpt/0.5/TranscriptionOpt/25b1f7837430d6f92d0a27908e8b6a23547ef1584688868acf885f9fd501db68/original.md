```
InfiniteOpt.add_point_variable(model::JuMP.Model,
                               var::InfiniteOpt.PointVariable,
                               key::Val{:TransData}
                               )::InfiniteOpt.GeneralVariableRef
```

Make a `PointVariableRef` and map it to the appropriate transcription variable and return the `GeneralVariableRef`. This is an extension of [`add_point_variable`](@ref InfiniteOpt.add_point_variable(::JuMP.Model,::Any,::Any, ::Any)) for `TranscriptionOpt`.
