```
read_rdata(path)
```

`.rdata` および `.rds` ファイルを DataFrame として読み込みます。`.rdata` ファイルは `Dict` になります。DataFrame は `result["name"]` で選択できます。

# 引数

  * `path`: ファイルの場所を示す文字列です。これはまだ URL からの読み込みをサポートしていません。
