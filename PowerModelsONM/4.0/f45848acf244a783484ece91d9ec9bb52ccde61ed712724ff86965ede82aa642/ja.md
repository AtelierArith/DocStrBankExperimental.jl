```
set_setting!(args::Dict{String,<:Any}, path::Tuple{Vararg{String}}, value::Any)
```

`path`に`value`を設定し、その後`args`からマルチネットワークデータを再生成するためのヘルパー関数です。
