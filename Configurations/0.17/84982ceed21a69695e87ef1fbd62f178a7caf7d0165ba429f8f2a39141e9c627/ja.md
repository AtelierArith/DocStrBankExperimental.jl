```
to_toml(x; sorted=false, by=identity, kw...)
```

オプション型のインスタンス `x` を TOML に変換し、`String` に書き込みます。`TOML.print` も参照してください。

`to_toml` は、デフォルトと同じ値を持つフィールドをエクスポートしません。これは、`include_defaults` を `true` に変更することで上書きできます。
