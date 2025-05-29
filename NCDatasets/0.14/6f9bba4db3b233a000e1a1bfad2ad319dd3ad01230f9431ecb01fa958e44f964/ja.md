```
ncgen(fname; ...)
ncgen(fname,jlname; ...)
```

NetCDFファイル`fname`と同じメタデータを持つJuliaコードを生成します。コードはファイル`jlname`に配置されるか、標準出力に印刷されます。デフォルトでは、新しいNetCDFファイルは`filename.nc`と呼ばれます。これはオプションのパラメータ`newfname`で変更できます。
