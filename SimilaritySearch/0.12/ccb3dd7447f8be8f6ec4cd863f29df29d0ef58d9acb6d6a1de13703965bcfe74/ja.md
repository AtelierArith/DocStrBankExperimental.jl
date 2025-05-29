```
neardup(idx::AbstractSearchIndex, ctx::AbstractContext, X::AbstractDatabase, ϵ::Real; k::Int=8, blocksize::Int=get_parallel_block(), minbatch=0, filterblocks=true, verbose=true)
neardup(dist::SemiMetric, X::AbstractDatabase, ϵ::Real; kwargs...)
```

データベース `X` で近似重複を見つけるために空のインデックス `idx` を使用します。アルゴリズムは、`X` の要素をインデックス化しようとし、`idx` のいくつかの要素に対して `ϵ` より近いアイテムは無視されます。

この関数は、名前付きタプル `(idx, map, nn, dist)` を返します。ここで：

  * `idx`: 重複していない要素のインデックスです
  * `ctx`: インデックスのコンテキスト
  * `map`: `|idx|-1` から `X` 内の位置へのマッピング
  * `nn`: $x \in X$ の各要素がそのカバー要素を指す配列（以前にインデックス化された要素 `u` で、$d(u, x_i) \leq ϵ$ となるもの）
  * `dist`: 各カバー要素への距離値の配列（`nn` の各要素に対応）

# 引数

  * `idx`: 空のインデックス（すなわち、`SearchGraph`）
  * `X`: 入力データセット
  * `ϵ`: 切り捨てる実数値。負の場合、`ϵ` は最近傍距離の小さなサンプルにおける 'abs(ϵ)' の分位値を使用して計算されます。分位法は、`ϵ` に対してあいまいな近似が必要なアプリケーションにのみ使用すべきです。

# キーワード引数

  * `k`: 取得する最近傍の数（いくつかのアルゴリズムは、より大きな `k` 値を取得することで利益を得ます）
  * `blocksize`: 一度に処理されるアイテムの数
  * `minbatch`: `@batch` マクロを制御するための引数（`Polyester` パッケージのマルチスレッドを参照）
  * `filterblocks`: true の場合、ブロック内の近似重複をフィルタリングします（`blocksize` パラメータを参照）。そうでない場合、ブロックは近似重複がないと仮定されます（例：ランダム化された順序）。
  * `verbose`: 関数の冗長性を制御します

# 注意事項

  * インデックス `idx` は増分構築をサポートする必要があります
  * オブジェクトの挿入をカスタマイズする必要がある場合、インデックス `idx` をラップし、カスタムメソッドを実装する必要があります。以下の関数の有効な実装が必要です：

      * `searchbatch(idx::AbstractSearchIndex, ctx, queries::AbstractDatabase, knns::Matrix, dists::Matrix)`
      * `distance(idx::AbstractSearchIndex)`
      * `length(idx::AbstractSearchIndex)`
      * `append_items!(idx::AbstractSearchIndex, ctx, items::AbstractDatabase)`
  * `database(idx)` を使用して 'ϵ-非重複要素の集合（$ϵ$-ネット）' にアクセスするか、`nn[i] == i` の場合にアクセスできます

```
