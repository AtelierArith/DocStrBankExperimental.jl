```julia
mutable struct ModelWrapper{M<:(Union{ModelWrappers.ModelName, P} where P), A<:NamedTuple, C<:NamedTuple, B<:ModelWrappers.ParameterInfo} <: BaytesCore.AbstractModelWrapper
```

Baytesモデル構造体。

現在のモデル値、名前、および情報に関する情報を含みます。詳細は[`ParameterInfo`](@ref)を参照してください。

# フィールド

  * `val::NamedTuple`: 現在のモデル値をNamedTupleとして保持 - ネストされたタプルで動作します。
  * `arg::NamedTuple`: トレースに保存する必要のない固定のログターゲット関数の補足引数。
  * `info::ModelWrappers.ParameterInfo`: パラメータ分布、変換、および制約に関する情報。詳細は[`ParameterInfo`](@ref)を参照してください。
  * `id::Union{ModelWrappers.ModelName, P} where P`: モデルID、デフォルトはBaseModel。ModelWrapper構造体のディスパッチに便利です。
