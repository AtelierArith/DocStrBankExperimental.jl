```
replace(o::CausalTable; kwargs...)
```

`CausalTable`オブジェクトのフィールドを提供されたキーワード引数で置き換えます。

# 引数

  * `o::CausalTable`: 置き換え対象の`CausalTable`オブジェクト。
  * `kwargs...`: フィールドの新しい値を指定するキーワード引数。

# 戻り値

指定されたフィールドが置き換えられた新しい`CausalTable`オブジェクト。
