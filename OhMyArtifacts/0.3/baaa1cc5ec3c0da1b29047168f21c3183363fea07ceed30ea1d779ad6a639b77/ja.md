```
load_my_artifacts_toml(artifacts_toml::String)
```

安全に `artifacts_toml` を読み取り、バインディング名から sha256 ハッシュへの `Dict{String, Any}` を返します。
