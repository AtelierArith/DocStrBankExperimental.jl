```
RSState{K}
```

RockSamplePOMDP問題における状態を表します。 `K`は岩の数を表す整数です。

# フィールド

  * `pos::RPos` ロボットの位置
  * `rocks::SVector{K, Bool}` 岩の状態（false=悪い、true=良い）
