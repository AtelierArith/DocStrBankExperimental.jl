特定のサービスをタイプで指定してモデルを確立します。キーワード引数 `use_service_name` を使用して、テンプレートの名前と同じ名前のサービスにモデルを割り当てます。キーワード引数 feedforward を使用して、シミュレーション時に操作モデル間で値を渡すことを可能にします。

# 引数

  * `::Type{D}`: 電力システムサービスタイプ - `::Type{B}`: 抽象サービス定式化

# 受け入れられるキーワード

  * `feedforward::Array{<:AbstractAffectFeedforward}` : モデル間でパラメータを渡すために使用
  * `use_service_name::Bool` : サービスの名前として名前を使用

# 例

reserves = ServiceModel(PSY.VariableReserve{PSY.ReserveUp}, RangeReserve)
