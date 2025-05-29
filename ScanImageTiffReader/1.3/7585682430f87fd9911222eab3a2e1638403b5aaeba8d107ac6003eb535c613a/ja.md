```
size(ctx::Context)
```

TIFFファイル内のデータの形状を返します。

# 例

```jldoctest
ScanImageTiffReader.open(mytif) do io
    size(io)
end
# 出力
(512, 512, 10)
```
