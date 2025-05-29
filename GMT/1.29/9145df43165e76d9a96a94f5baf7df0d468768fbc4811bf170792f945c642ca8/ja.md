```
I = ind2rgb(I::GMTimage, cpt::GMTcpt=GMTcpt(), layout="BRPa"; cmap=GMTcpt())
```

インデックス画像 I を RGB に変換します。`cmap` が提供されていない場合、内部カラーマップを使用して変換を行います。どちらも存在しない場合、レイヤーは 3 回複製され、グレースケール画像が生成されます。

`cpt` の位置引数の代わりに `cmap` キーワードを使用してください。
