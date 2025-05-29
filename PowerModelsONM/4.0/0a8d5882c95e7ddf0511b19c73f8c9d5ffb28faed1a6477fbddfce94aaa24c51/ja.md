```
get_setting(args::Dict{String,Any}, path::Tuple{Vararg{String}}, default::Any=missing)::Any
```

任意のネストされたパスで`args`辞書内の設定プロパティを取得するためのヘルパー関数であり、パスが存在しない場合はデフォルト値を返します。
