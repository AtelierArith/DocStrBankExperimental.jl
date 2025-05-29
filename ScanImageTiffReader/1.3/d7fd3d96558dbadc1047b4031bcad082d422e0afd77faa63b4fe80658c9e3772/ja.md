```
length(ctx::Context)
```

画像スタック内の平面の数を返します。

# 例

```jldoctest
ScanImageTiffReader.open(mytif) do io
    length(io)
end
# 出力
10
```
