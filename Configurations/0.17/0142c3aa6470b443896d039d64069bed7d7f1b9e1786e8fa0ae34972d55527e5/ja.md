```
to_toml([f::Function], filename::String, option; sorted=false, by=identity, kw...)
```

オプション型のインスタンス `option` を TOML に変換し、`filename` に書き込みます。`TOML.print` も参照してください。
