```
select(o::CausalTable, symbols)
```

`CausalTable`オブジェクトから指定された列を選択します。

# 引数

  * `o::CausalTable`: 列を選択するための`CausalTable`オブジェクト。
  * `symbols`: 選択する列を表すシンボルのリスト。

# 戻り値

  * 選択された列のみを含む新しい`CausalTable`オブジェクト。
