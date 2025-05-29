```
partial_transpose(shadow::DenseShadow, subsystem::Vector{Int})::DenseShadow
```

指定されたサブシステムに対して、各サイトについて未プライムインデックスとそのプライムパートナーを入れ替えることによって、DenseShadowの部分転置を計算します。これは、基礎となるITensorのビューを返す`swapind`関数を使用して行われます。

# 引数

  * `shadow::DenseShadow`: 密な古典的シャドウ。
  * `subsystem::Vector{Int}`: 部分転置を実行するための1ベースのサイトインデックスのベクトル。

# 戻り値

指定されたサイトが部分転置された新しいDenseShadow。
