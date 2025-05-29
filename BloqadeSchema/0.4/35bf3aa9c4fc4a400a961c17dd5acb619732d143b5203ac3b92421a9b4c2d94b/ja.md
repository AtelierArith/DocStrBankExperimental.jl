```
struct SchemaTranslationParams
```

ハミルトニアンを実行する回数と、ハミルトニアンが実行されるマシンの能力を、ハミルトニアンを他の形式に変換する関数への引数として指定するために使用されます。

関連情報としては、[`to_schema`](@ref)、[`to_dict`](@ref)、[`to_json`](@ref)があります。

# フィールド

  * `nshots::Int = 1`: ハミルトニアンを実行する回数
  * `device_capabilities::DeviceCapabilities = get_device_capabilities()`: ハミルトニアンが実行されるマシンの能力
