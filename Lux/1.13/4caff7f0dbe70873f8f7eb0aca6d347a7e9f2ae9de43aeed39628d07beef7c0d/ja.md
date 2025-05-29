```
VariationalHiddenDropout(p; dims=:)
```

VariationalHiddenDropoutレイヤー。Dropoutとの唯一の違いは、`mask`が[`Lux.update_state(l, :update_mask, Val(true))`](@ref)が呼び出されるまで保持されることです。

## 引数

  * `p`: Dropoutの確率（`p = 0`の場合は[`NoOpLayer`](@ref)が返されます）

## キーワード引数

  * 特定の次元でドロップアウトを適用するには、`dims`キーワードを指定します。例えば、`VariationalHiddenDropout(p; dims = 3)`は、WHCN入力の全チャネルをランダムにゼロにします（これを2Dドロップアウトとも呼びます）。

## 入力

  * `x`: AbstractArrayでなければなりません

## 戻り値

  * `training=Val(true)`の場合はドロップアウトマスクが適用された`x`、それ以外の場合は単に`x`
  * 更新された`rng`を持つ状態

## 状態

  * `rng`: 擬似乱数生成器
  * `training`: トレーニング/推論モードを確認するために使用されます
  * `mask`: ドロップアウトマスク。初期状態は何も設定されていません。各実行後、その呼び出しで適用されたマスクを含みます
  * `update_mask`: 現在の呼び出しで新しいマスクを生成する必要があるかどうかを格納します

[`Lux.testmode`](@ref)を呼び出してテストモードに切り替えます。

他にも[`AlphaDropout`](@ref)、[`Dropout`](@ref)を参照してください。
