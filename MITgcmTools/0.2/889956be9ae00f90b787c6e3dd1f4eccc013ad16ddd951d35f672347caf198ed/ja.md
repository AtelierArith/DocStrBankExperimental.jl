```
read_meta(metafile)
```

`MITgcm` メタデータファイルを読み込み、解析して NamedTuple として返します。

```
p="./hs94.cs-32x32x5/run/"
meta=read_meta(p*"surfDiag.0000000020.002.001.meta")
pairs(meta)
meta.dimList
```
