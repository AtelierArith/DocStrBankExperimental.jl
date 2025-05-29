```
partial_transpose(shadow::FactorizedShadow, subsystem::Vector{Int})::FactorizedShadow
```

指定されたサブシステムに対して、各サイトの未プライムインデックスとプライムインデックスを `swapind` 関数を使用して入れ替えることによって、FactorizedShadow の部分転置を計算します。この関数は、不要なデータの重複を避けるために、基盤となる ITensors のビューを返します。

# 引数

  * `shadow::FactorizedShadow`: 因子化された古典的シャドウ。
  * `subsystem::Vector{Int}`: 部分転置を実行するための1ベースのサイトインデックスのベクトル。

# 戻り値

指定されたサイトが部分転置された新しい FactorizedShadow。
