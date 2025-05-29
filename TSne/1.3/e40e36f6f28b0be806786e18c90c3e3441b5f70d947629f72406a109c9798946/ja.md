```
tsne(X::Union{AbstractMatrix, AbstractVector}, ndims::Integer=2, reduce_dims::Integer=0,
     max_iter::Integer=1000, perplexity::Number=30.0; [keyword arguments])
```

`t-SNE`（t-分布確率的近傍埋め込み）を`X`に適用し、すなわちその点（行）を`ndims`次元に埋め込み、近くの隣人を保持します。

計算された埋め込み座標の点×`ndims`行列を返します。

元の実装とは異なり、デフォルトではPCAを初期化に使用しません。

### 引数

  * `distance` `true`の場合、`X`が距離行列であることを指定します。`Function`または`Distances.SemiMetric`の型の場合、`X`の行（または要素、`X`がベクトルの場合）間の距離を計算するために使用する関数を指定します。
  * `reduce_dims` t-SNEに使用する`X`のPCAの最初の次元の数。0の場合、すべての利用可能な次元が使用されます。
  * `pca_init` `X`の最初の`ndims`のPCAを初期t-SNEレイアウトとして使用するかどうか。`false`（デフォルト）の場合、メソッドはランダムレイアウトで初期化されます。
  * `max_iter` t-SNEの反復回数。
  * `perplexity` データポイントの「効果的な隣人」の数。典型的な値は5から50の範囲で、デフォルトは30です。
  * `verbose` 情報および診断メッセージを出力します。
  * `progress` t-SNE最適化中に進捗メーターを表示します。
  * `min_gain`, `eta`, `initial_momentum`, `final_momentum`, `momentum_switch_iter`, `stop_cheat_iter`, `cheat_scale` t-SNE最適化の低レベルパラメータ。
  * `extended_output` `true`の場合、埋め込み座標行列、点のパープレキシティ、および最終的なクルバック・ライブラー発散のタプルを返します。

[元のt-SNE実装](https://lvdmaaten.github.io/tsne)も参照してください。
