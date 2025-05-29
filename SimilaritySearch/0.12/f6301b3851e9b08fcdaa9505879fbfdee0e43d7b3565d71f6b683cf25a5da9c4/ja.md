```
struct SearchGraph <: AbstractSearchIndex
```

SearchGraph インデックス。距離関数 `dist` を通じて比較可能な点のセットを格納します。パフォーマンスは検索アルゴリズム `algo` と近傍ポリシーによって決まります。挿入が行われる際にパラメータを調整するためのコールバックをサポートしています。

  * `hints`: 探索のための初期点（空のヒントはランダムな点を使用することを意味します）

注意: 並列挿入は `append!` または `index!` 関数を通じて `parallel_block > 1` で行うべきです。
