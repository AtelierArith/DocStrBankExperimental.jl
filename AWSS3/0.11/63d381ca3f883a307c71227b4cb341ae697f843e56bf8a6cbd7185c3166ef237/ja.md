```
read(fp::S3Path; byte_range=nothing)
```

S3パスからデータを`Vector{UInt8}`として取得します。オブジェクトのサブセットは`byte_range`で指定でき、これは連続した整数範囲である必要があります。例：`1:4`。
