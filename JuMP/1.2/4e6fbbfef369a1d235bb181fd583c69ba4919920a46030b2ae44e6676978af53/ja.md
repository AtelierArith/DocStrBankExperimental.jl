```
read_from_file(
    filename::String;
    format::MOI.FileFormats.FileFormat = MOI.FileFormats.FORMAT_AUTOMATIC,
    kwargs...,
)
```

`filename`から`format`の形式でJuMPモデルを読み込みます。

ファイル名が`.gz`で終わる場合、Gzipを使用して解凍されます。ファイル名が`.bz2`で終わる場合、BZip2を使用して解凍されます。

他の`kwargs`は、選択した形式の`Model`コンストラクタに渡されます。
