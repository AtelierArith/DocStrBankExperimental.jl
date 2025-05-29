```
cref=add_sum!(graph,node,c,nodelist,base_name=node)
```

`nodelist::Vector`で与えられた2つ以上のノードの線形結合を、`c`で与えられた係数を使って追加します。`base_name`は合計のための一時変数です。合計は`node`に格納されます。

参照のリスト`cref`を返します。
