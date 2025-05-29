```
root!(tree::Tree, node::AbstractString; root_on_leaf, time=0., remove_singletons=true)
```

`tree`を`tree.lnodes[node]`でルートします。これは外群のルーティングに相当します。`time`がゼロでない場合、`node`の上に高さ`time`でルートし、新しいノードを挿入します。

`remove_singletons`が真の場合、再ルーティング後にシングルトンノードが削除されます。これは、古いルートを削除するのに役立ちます。古いルートはしばしばシングルトンになってしまうためです。
