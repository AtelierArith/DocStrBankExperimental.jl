```
convertsolution(rawsolution::OrderedDict{Int,Int}, vardata::VariableData)::OrderedDict{String,String}
```

変数からその値へのマッピングの形で解を返します（両方とも文字列として）。

# 注意事項

  * `Int=>Int` の解を `String=>String` の解に変換するには、`vardata` に定義された `inverse*` マッピングを使用します。
