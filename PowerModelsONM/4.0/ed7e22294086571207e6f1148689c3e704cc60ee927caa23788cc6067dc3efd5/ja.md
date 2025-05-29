```
build_settings_file(
    network_file::String,
    settings_file::String="settings.json";
    kwargs...
)
```

ONMで使用するために、ネットワークデータ構造`eng::Dict{String,<:Any}`から`io`に設定構造体を書き込むためのヘルパー関数です。
