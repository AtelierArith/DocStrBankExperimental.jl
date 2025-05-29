```
determine_partition(trajectory, tree_type::Tree{Val{true}, S}; override = false) where S
```

# 説明

この関数は、状態空間のパーティショニングをバイナリツリーに決定します。ツリーは、状態空間を2つの部分に再帰的に分割することによって決定されます。分割はk-meansクラスタリングによって行われます。ツリーのレベル数は`levels`キーワード引数によって決定されます。軌道が長すぎる場合、各レベルあたり約1000ポイントに切り詰められます。`override`キーワード引数を使用して、この動作を上書きすることができます。

# 引数

  * `trajectory`: 状態の軌道
  * `tree_type`: `Tree`型

# キーワード引数

  * `override`: 軌道の切り詰めを上書きするかどうかを示すブール値

# 戻り値

  * `embedding`: `Tree`オブジェクト
