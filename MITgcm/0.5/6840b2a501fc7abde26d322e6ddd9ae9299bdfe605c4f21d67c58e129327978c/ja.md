```
read_mdsio(fil::String)
```

単一の `MITgcm` MDSIOタイプファイル（".data" バイナリ + ".meta" テキストペア）を読み込み、配列として返します。

```
p="./hs94.cs-32x32x5/run/"
x=read_mdsio(p*"surfDiag.0000000020.002.001.data")
y=read_mdsio(p*"pickup.ckptA.002.001.data")
z=read_mdsio(p*"T.0000000000.002.001.data")
```
