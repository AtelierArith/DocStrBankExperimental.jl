```
InfiniteOpt.add_point_variable(model::JuMP.Model,
                               var::InfiniteOpt.PointVariable,
                               key::Val{:TransData}
                               )::InfiniteOpt.GeneralVariableRef
```

`PointVariableRef`を作成し、適切なトランスクリプション変数にマッピングして`GeneralVariableRef`を返します。これは[`add_point_variable`](@ref InfiniteOpt.add_point_variable(::JuMP.Model,::Any,::Any, ::Any))の`TranscriptionOpt`への拡張です。
