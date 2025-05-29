```
PointVariable{I <: GeneralVariableRef} <: JuMP.AbstractVariable
```

ポイント変数情報を格納するための`DataType`です。`parameter_values`フィールドの要素は、[`InfiniteVariable`](@ref)で定義されたパラメータ参照タプルの形式と一致する必要があります。

**フィールド**

  * `info::JuMP.VariableInfo{Float64, Float64, Float64, Float64}`: JuMP変数情報。
  * `infinite_variable_ref::I`: ポイント変数に関連付けられた無限変数/導関数参照。
  * `parameter_values::Vector{Float64}`: ポイントを定義する無限パラメータ値。
