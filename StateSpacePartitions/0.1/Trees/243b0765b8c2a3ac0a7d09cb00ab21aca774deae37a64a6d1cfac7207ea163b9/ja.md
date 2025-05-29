```
determine_partition(trajectory, tree_type::Tree{Val{false}, S}; override = false) where S
```

# 説明

この関数は、軌道を非構造化ツリーに分割します。ツリー構造は`tree_type`引数によって指定されます。`trajectory`引数は状態の軌道です。`override`キーワード引数は、軌道の切り捨てを上書きするかどうかを示すブール値です。

# 引数

  * `trajectory`: 状態の軌道
  * `tree_type`: `Tree`型

# キーワード引数

  * `override`: 軌道の切り捨てを上書きするかどうかを示すブール値

# 戻り値

  * `embedding`: `Tree`オブジェクト
