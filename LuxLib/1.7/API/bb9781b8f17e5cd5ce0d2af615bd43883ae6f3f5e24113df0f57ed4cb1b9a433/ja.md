```
dropout(rng::AbstractRNG, x, p, training, invp, dims)
dropout(rng::AbstractRNG, x, mask, p, training, update_mask::Union{Val, StaticBool},
    invp, dims)
```

ドロップアウト: ニューラルネットワークの過学習を防ぐためのシンプルな方法。詳細は [srivastava2014dropout](@citet) を参照してください。

## 引数

  * `rng`: 擬似乱数生成器
  * `x`: 入力配列
  * `mask`: ドロップアウトマスク。使用しない場合は自動的に構築されます
  * `p`: 要素がドロップアウトされる確率
  * `training`: トレーニングモードで実行している場合は `Val(true)` または `True()` に設定します。自動微分コンテキスト内で関数が呼び出されているかどうかを自動的に判断するために `nothing` に設定できます
  * `update_mask`: `Val(true)` または `True()` の場合、マスクが生成されて使用されます。それ以外の場合、提供された `mask` が直接使用されます
  * `invp`: マスクに掛けられる逆数。`invp = 1 / (1 - p)` として計算されます。

## 戻り値

  * ドロップアウトを適用した後の出力配列
  * ドロップアウトマスク（`training == false` の場合、返される値は無意味です）
  * 擬似乱数生成器の更新された状態
