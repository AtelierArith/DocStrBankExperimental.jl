```
read_mnc(pth::String,fil::String,var::String)
```

変数 `var` を一連の `MITgcm` MNCタイプのファイル（ネットCDFファイル）から読み込み、結合して配列として返します。このメソッドは、`pth` 内で `fil` で始まるファイルを検索します。
