```julia
set_device_model!(
    template::SiennaPRASInterface.RATemplate,
    _::Type{D<:PowerSystems.Device},
    _::Type{B<:SiennaPRASInterface.AbstractRAFormulation}
) -> Vector{SiennaPRASInterface.DeviceRAModel}

```

# 引数

  * `template::RATemplate`: デバイスモデルを追加するためのテンプレート
  * `::Type{D}`: デバイスタイプ
  * `::Type{B}`: 定式化タイプ

コンストラクタにタイプを渡すことで、RATemplateにデバイスモデルを追加します。
