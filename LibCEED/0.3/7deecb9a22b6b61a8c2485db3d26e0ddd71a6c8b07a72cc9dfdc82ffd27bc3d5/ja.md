```
トポロジー
```

非テンソルH1要素基底を作成するための基底形状のタイプ。`LINE`、`TRIANGLE`、`QUAD`、`TET`、`PYRAMID`、`PRISM`、または`HEX`のいずれか。

次のビットシフトを使用して次元を抽出できます：

```
dim = Int(topology) >> 16
```
