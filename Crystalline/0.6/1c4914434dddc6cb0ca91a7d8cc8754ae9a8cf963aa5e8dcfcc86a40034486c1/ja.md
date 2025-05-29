```
pointgroup(pgnum::Integer, ::Union{Val{D}, Integer}=Val(3), setting::Integer=1)
                                                                  -->  PointGroup{D}
```

与えられた標準番号 `pgnum` に関連付けられた対称操作を、次元 `D` の `PointGroup{D}` として返します。点群の番号付けとその IUC ラベルとの関係は `Crystalline.PG_NUM2IUC[D]` および `Crystalline.IUC2NUM[D]` に列挙されています。

特定の点群は複数の設定バリアントに登場します。例えば、IUC ラベル 321 と 312 はどちらも `pgnum = 18` に対応し、異なる2つの設定で表現された同じ群構造に対応します。`setting` 引数は、これらの設定のバリエーションの間で選択することを可能にします。
