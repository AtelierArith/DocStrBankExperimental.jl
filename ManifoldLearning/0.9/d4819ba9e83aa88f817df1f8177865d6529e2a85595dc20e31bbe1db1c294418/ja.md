```
fit(TSNE, data; p=30, maxoutdim=2, kwargs...)
```

`t-SNE` モデルを `data` にフィットさせます。

# 引数

  * `data`: 観測値の行列。`data` の各列は観測値です。

# キーワード引数

  * `p`: パープレキシティパラメータ (*デフォルト* `30`)。
  * `maxoutdim`: 縮小空間の次元 (*デフォルト* `2`)。
  * `maxiter`: 探索アルゴリズムの総反復回数 (*デフォルト* `800`)。
  * `exploreiter`: 探索アルゴリズムの探索段階の反復回数 (*デフォルト* `200`)。
  * `tol`: 許容閾値 (*デフォルト* `1e-7`)。
  * `exaggeration`: 元の空間と縮小空間の間のタイトネス制御パラメータ (*デフォルト* `12`)。
  * `initialize`: 埋め込みの初期化パラメータ (*デフォルト* `:pca`)。
  * `rng`: 初期埋め込みの初期化のための乱数生成オブジェクト。
  * `nntype`: 最近傍構築クラス (`AbstractNearestNeighbors` から派生)。

# 例

```julia
M = fit(TSNE, rand(3,100)) # t-SNE モデルを構築
R = predict(M)             # 次元削減を実行
```
