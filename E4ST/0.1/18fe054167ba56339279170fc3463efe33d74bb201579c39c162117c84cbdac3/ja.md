```
add_nominal_load!(config, data)
```

`config[:load_add_file]`にある負荷電力を、[`match_nominal_load!`](@ref)での年次マッチの後に負荷要素に追加します。

マッチの後に追加の負荷を提供して、差を比較したい場合があります。
