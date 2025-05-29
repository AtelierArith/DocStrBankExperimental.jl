```
add_option!(opts::JutulConfig, :my_cool_option, 3, "My option has this brief description")
```

既存の [`JutulConfig`](@ref) 構造体にオプションを追加します。追加の現在文書化されていないキーワード引数を使用して、有効な型と値を制限することができます。
