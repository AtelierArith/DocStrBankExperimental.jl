```
write_to_file(
    model::Model,
    filename::String;
    format::MOI.FileFormats.FileFormat = MOI.FileFormats.FORMAT_AUTOMATIC,
    kwargs...,
)
```

JuMPモデル`model`を`filename`に`format`形式で書き込みます。

ファイル名が`.gz`で終わる場合、Gzipを使用して圧縮されます。ファイル名が`.bz2`で終わる場合、BZip2を使用して圧縮されます。

他の`kwargs`は、選択した形式の`Model`コンストラクタに渡されます。
