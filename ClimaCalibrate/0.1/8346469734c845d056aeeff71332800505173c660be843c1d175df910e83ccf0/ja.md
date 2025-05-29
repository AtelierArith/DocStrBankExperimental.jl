```
get_prior(param_dict::AbstractDict; names = nothing)
get_prior(prior_path::AbstractString; names = nothing)
```

`param_dict` または `prior_path` で指定された TOML 設定ファイルから結合された事前分布を構築します。`names` が提供されている場合は、そのパラメータのみが使用されます。
