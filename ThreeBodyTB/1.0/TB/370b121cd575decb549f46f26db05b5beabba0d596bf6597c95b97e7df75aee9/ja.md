```
function read_tb_crys(filename, tbc::tb_crys)
```

`filename` から `tb_crys` オブジェクトを読み込み、返します。 `write_tb_crys` を参照してください。

`"filename"` が見つからない場合は、`"filename.xml"`、`"filename.gz"`、`"filename.xml.gz"` を探します。

gzipped ファイルを直接読み込むことができます。
