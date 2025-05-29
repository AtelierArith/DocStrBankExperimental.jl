```
get_option(network::Dict{String,<:Any}, path::Tuple{Vararg{String}}, default::Any=missing)::Any
```

ネットワーク辞書内の任意のネストされたパスにあるプロパティを取得するためのヘルパー関数であり、パスが存在しない場合はデフォルト値を返します。
