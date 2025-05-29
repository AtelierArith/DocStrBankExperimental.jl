```
read_meta(pth::String,fil::String)
```

`MITgcm` メタデータファイルを読み込み、解析して、NamedTuple の配列として返します。

```
p="./hs94.cs-32x32x5/run/"
meta=read_meta(p,"surfDiag.0000000020")
pairs(meta[end])
[meta[i].dimList for i in 1:length(meta)]
```
