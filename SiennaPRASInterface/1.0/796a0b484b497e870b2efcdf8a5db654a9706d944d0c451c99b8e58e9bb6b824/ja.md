```julia
set_device_model!(
    template::SiennaPRASInterface.RATemplate,
    device_model::SiennaPRASInterface.DeviceRAModel{D}
) -> Vector{SiennaPRASInterface.DeviceRAModel}

```

# 引数

  * `template::RATemplate`: デバイスモデルを追加するためのテンプレート
  * `device_model::DeviceRAModel{D}`: 追加するデバイスモデル

RATemplateにデバイスモデルを追加します。既存のモデルが指定されたデバイスタイプに既に適用されている場合は、警告が発行されます。ただし、新しいモデルが優先されます。
