```
partial_transpose(shadow::AbstractShadow, subsystem::Vector{Int})
```

指定されたサブシステムに対してシャドウオブジェクトの部分転置を計算します。この操作はQuTiPの部分転置メソッドに類似しています。

# 引数

  * `shadow::AbstractShadow`: 部分転置が計算されるシャドウオブジェクト。
  * `subsystem::Vector{Int}`: 転置を実行するサブシステムを指定するサイトインデックスのベクター（1ベース）。

# 戻り値

入力の部分転置である新しいシャドウオブジェクト。

# 例

```julia
transposed_shadow = partial_transpose(shadow, [2, 4])
```
