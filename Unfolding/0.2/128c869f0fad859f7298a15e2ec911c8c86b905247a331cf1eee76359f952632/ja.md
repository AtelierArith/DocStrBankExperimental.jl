```
unfold(to_unf, ref, unf_ref; optim=:default)
```

入力点 `to_unf` を、すでに展開された点 `unf_ref` と元の空間における対応点 `ref` に基づいて展開します。例えば、ドメインがすでに展開された後にサンプルを展開するのに便利です。展開された点の座標行列を返します。もし `to_unf` が点のリストであれば、行列のタプルを返します。

## パラメータ:

  * `to_unf`  - 展開される点を持つ座標行列
  * `ref`     - 展開のための参照点を持つ座標行列
  * `unf_ref` - 展開された参照点を持つ座標行列
  * `optim`   - 最適化ステップのための追加パラメータ; :default または以下に示すキーを持つ NamedTuple のいずれか

### `optim` パラメータ:

*デフォルト:* optim = (search=:knn, neigh=50, maxerr=5, nchunks=1)

  * `search`  - ローカル最適化のための検索タイプ (:knn は k-最近傍、:radius は半径検索)。
  * `neigh`   - ローカル最適化のための隣接点の数 (search=:knn の場合) または半径距離 (search=:radius の場合)。
  * `maxerr`  - 展開最適化のために受け入れられる最大歪み。
  * `nchunks` - 最適化のラウンド数。
