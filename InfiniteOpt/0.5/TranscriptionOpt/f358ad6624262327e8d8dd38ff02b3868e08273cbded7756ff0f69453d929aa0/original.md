```
InfiniteOpt.add_semi_infinite_variable(model::JuMP.Model,
                                 var::InfiniteOpt.SemiInfiniteVariable,
                                 key::Val{:TransData}
                                 )::InfiniteOpt.GeneralVariableRef
```

Make a `SemiInfiniteVariableRef` and add `var` to the transcription data  and return the `GeneralVariableRef`. This is an extension of  [`add_semi_infinite_variable`](@ref InfiniteOpt.add_semi_infinite_variable(::JuMP.Model,::Any,::Any))  for `TranscriptionOpt`. Note that `internal_semi_infinite_variable` is also  extended to be able to access the `var`.
