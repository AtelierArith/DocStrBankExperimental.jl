```
unfold(ref, to_unf, samps=nothing; isomap=:default, optim=:default)
```

入力点 `to_unf` を参照点 `ref` に基づいて展開します。展開された点の座標行列を返します。あるいは、`to_unf` が点のリストである場合は行列のタプルを返します。

## パラメータ:

  * `to_unf`  - 展開される点を持つ座標行列
  * `ref`     - 展開のための参照点を持つ座標行列
  * `isomap`  - isomap ステップの追加パラメータ; :default または以下に示すキーを持つ NamedTuple
  * `optim`   - 最適化ステップの追加パラメータ; :default または以下に示すキーを持つ NamedTuple

### `isomap` パラメータ:

*デフォルト:* isomap = (search=:knn, neigh=16, anchors=1500, reftol=0.01)

  * `search`  - Isomap の近傍グラフを構築するための検索タイプ (:knn は k-最近傍、:radius は半径検索)。
  * `neigh`   - Isomap の近傍グラフを構築するための近傍の数 (search=:knn の場合) または半径距離 (search=:radius の場合)。
  * `anchors` - ランドマーク isomap のためのアンカーの数
  * `reftol`  - 参照点が重複と見なされる距離

### `optim` パラメータ:

*デフォルト:* optim = (search=:knn, neigh=50, maxerr=5, nchunks=4)

  * `search`  - ローカル最適化のための検索タイプ (:knn は k-最近傍、:radius は半径検索)。
  * `neigh`   - ローカル最適化のための近傍の数 (search=:knn の場合) または半径距離 (search=:radius の場合)。
  * `maxerr`  - 展開最適化のために受け入れられる最大歪み。
  * `nchunks` - 最適化のラウンド数。
