```
partial_trace(shadow::DenseShadow, subsystem::Vector{Int})
```

指定されたサブシステムの補集合に対して `DenseShadow` オブジェクトの部分トレースを計算します。

# 引数

  * `shadow::DenseShadow`: 部分トレースを計算するための密なシャドウ。
  * `subsystem::Vector{Int}`: 保持するサブシステムを指定するサイトインデックスのベクトル（1ベース）。

# 戻り値

指定されたサブシステムに減少した新しい `DenseShadow` オブジェクト。
