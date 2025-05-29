```
reject(o::CausalTable, symbols)
```

`CausalTable`オブジェクト`o`から`symboils`で指定された列を削除します。

# 引数

  * `o::CausalTable`: シンボルが拒否される`CausalTable`オブジェクト。
  * `symbols`: `CausalTable`から拒否されるシンボルのコレクション。

# 戻り値

指定されたシンボルがデータから削除された新しい`CausalTable`オブジェクト。
