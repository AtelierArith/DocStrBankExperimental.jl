```
load_configs(filename; format=:binary, bitlength=nothing, num_flavors=2)
```

ファイル `filename` から設定を読み込みます。フォーマットは `:binary` または `:text` です。フォーマットが `:binary` の場合、ビット列の長さ `bitlength` を指定する必要があり、`num_flavors` は自由度を指定します。
