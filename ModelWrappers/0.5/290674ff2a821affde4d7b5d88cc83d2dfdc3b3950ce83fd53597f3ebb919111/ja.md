```julia
struct Tagged{A<:NamedTuple, B<:ModelWrappers.ParameterInfo}
```

モデルパラメータのサブセットに関する情報を格納します。

# フィールド

  * `parameter::NamedTuple`: ModelWrapperパラメータ名のサブセット。
  * `info::ModelWrappers.ParameterInfo`: パラメータ分布、変換、および制約のサブセットに関する情報、詳細は[`ParameterInfo`](@ref)を参照してください。
