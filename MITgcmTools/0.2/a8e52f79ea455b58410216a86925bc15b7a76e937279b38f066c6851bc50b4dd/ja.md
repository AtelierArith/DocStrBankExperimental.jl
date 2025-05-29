```
read_mdsio(pth::String,fil::String)
```

`MITgcm` MDSIOタイプのファイル（".data" バイナリ + ".meta" テキストペア）のセットを読み込み、結合して配列として返します。`fil`が完全なファイル名である`read_mdsio(fil::String)`とは異なり、このメソッドは`pth`内で`fil`で始まるファイルを検索します。

```
p="./hs94.cs-32x32x5/run/"
x=read_mdsio(p,"surfDiag.0000000020")
y=read_mdsio(p,"pickup.ckptA")
z=read_mdsio(p,"T.0000000000")
```
