```
current_parameter(ds::DynamicalSystem, index [,p])
```

`ds`に対応する特定のパラメータを返します。`index`は[`set_parameter!`](@ref)に与えられる任意のものであり、`p`は[`current_parameters`](@ref)にデフォルト設定されており、パラメータを抽出するためのパラメータコンテナです。これはデフォルト値とレイアウトが一致する必要があります。

付随する名前には[`parameter_name`](@ref)を使用してください。
