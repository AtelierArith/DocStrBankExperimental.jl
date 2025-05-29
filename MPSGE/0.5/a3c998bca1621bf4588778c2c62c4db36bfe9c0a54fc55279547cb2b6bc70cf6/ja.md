```
cost_function(S::ScalarSector; virtual = false)
cost_function(S::ScalarSector, nest::Symbol; virtual = false)
```

与えられたセクターとネストのコスト関数のベクトルを返します。`nest`が提供されていない場合は、入力ツリーのコスト関数を返します。

`nest`はネストを表すシンボルです。これは商品名であることもあります。

`virtual`がtrueの場合、仮想コスト関数を返します。
