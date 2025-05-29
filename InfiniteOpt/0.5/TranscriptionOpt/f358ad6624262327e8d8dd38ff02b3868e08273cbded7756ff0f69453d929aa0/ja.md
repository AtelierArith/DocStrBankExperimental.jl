```
InfiniteOpt.add_semi_infinite_variable(model::JuMP.Model,
                                 var::InfiniteOpt.SemiInfiniteVariable,
                                 key::Val{:TransData}
                                 )::InfiniteOpt.GeneralVariableRef
```

`SemiInfiniteVariableRef`を作成し、`var`を転写データに追加して`GeneralVariableRef`を返します。これは[`add_semi_infinite_variable`](@ref InfiniteOpt.add_semi_infinite_variable(::JuMP.Model,::Any,::Any))の`TranscriptionOpt`への拡張です。`internal_semi_infinite_variable`も`var`にアクセスできるように拡張されていることに注意してください。
