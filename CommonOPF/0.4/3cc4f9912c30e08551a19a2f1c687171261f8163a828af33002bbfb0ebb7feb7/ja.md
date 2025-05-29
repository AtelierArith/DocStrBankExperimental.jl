```
trim_tree_once!(net::Network)
```

`trim_tree!`のサポート関数である`trim_tree_once!`は、すべての空のリーフバスを削除します。ツリーをトリミングする際に、新しいリーフが作成されることがあります。そのため、`trim_tree!`は`trim_tree_once!`をループします。
