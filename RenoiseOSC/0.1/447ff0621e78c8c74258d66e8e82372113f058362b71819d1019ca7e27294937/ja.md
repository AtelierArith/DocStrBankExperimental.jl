```
setparam(key::Union{AbstractString,Integer}, value::Real; track::Integer=-1, device::Integer=-1)
```

デバイスの名前またはインデックスによって、任意のデバイスのパラメータを設定します。`value`は`0.0`と`1.0`の間に制限されます。指定されていない場合、trackとdeviceは現在選択されているトラックとデバイスにデフォルト設定されます。
