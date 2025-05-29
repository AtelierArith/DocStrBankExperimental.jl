```
permute_ped!(invp, pedlist [,idtable])
```

この関数は、動物を置換ベクトルによって「再番号付け」します。`pedlist`内のコードを、`invp`内の置換リストに従って更新します。これは`invp[oldid]=newid`の形で、`find_ped_order`のような関数によって生成されます。この関数は、`idtable`内のIDも置き換えます（オプション）。未知の親グループのコードは、通常、実際の動物の最大IDよりも大きく、新しい系図に残ります。
