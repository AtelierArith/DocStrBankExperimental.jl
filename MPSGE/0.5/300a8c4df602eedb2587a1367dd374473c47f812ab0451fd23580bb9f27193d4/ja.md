```
revenue_function(S::ScalarSector; virtual = false)    
revenue_function(S::ScalarSector, nest::Symbol; virtual = false)
```

与えられたセクターとネストの収益関数のベクトルを返します。`nest`が提供されていない場合は、入力ツリーの収益関数を返します。

`nest`はネストを表すシンボルです。これは商品名であることもあります。

`virtual`がtrueの場合、仮想収益関数を返します。
