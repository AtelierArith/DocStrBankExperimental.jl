```
pxtype(ctx::Context)
```

TIFFファイル内のデータの型を返します。

# 例

```jldoctest
ScanImageTiffReader.open(mytif) do io
    pxtype(io)
end
# 出力
Int16
```
