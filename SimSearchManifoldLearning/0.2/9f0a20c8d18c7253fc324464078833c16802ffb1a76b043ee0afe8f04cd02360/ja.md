```
predict(model::UMAP, Q::AbstractDatabase; k::Integer=15, kwargs...)
predict(model::UMAP, knns, dists; <kwargs>) -> embedding
```

与えられたモデルを使用して、新しいポイント $Q$ を $(X, dist)$ によって生成された既存の埋め込みに埋め込みます。2番目の関数は、ある距離関数の下で `X` における `Q` の `k` 最近傍を使用して表現します（`knns` と `dists`）。両方を計算するには `SimilaritySearch` の `searchbatch` を参照してください（`AbstractDatabase` オブジェクトについても）。

# 引数

  * `model`: フィッティングされたモデル
  * `knns`: サイズ $(k, |Q|)$ の識別子（整数）の行列
  * `dists`: サイズ $(k, |Q|)$ の距離（浮動小数点値）の行列

注意: 近傍の数 `k`（knn 行列に埋め込まれた）は埋め込みを制御します。大きな値はデータのよりグローバルな構造を捉え、小さな値はよりローカルな構造を捉えます。

# キーワード引数

  * `n_epochs::Integer = 30`: 埋め込み最適化のためのトレーニングエポックの数
  * `learning_rate::Real = 1`: 最適化中の初期学習率
  * `learning_rate_decay::Real = 0.8`: `learning_rate` パラメータの減衰係数（各エポックで）
  * `set_operation_ratio::Real = 1`: UMAP グラフを構築する際にファジー集合の和とファジー集合の交差の間を補間します（グローバルファジー単体集合）。このパラメータの値は 1.0 と 0.0 の間であるべきです: 1.0 は純粋なファジー和を示し、0.0 は純粋なファジー交差を示します。
  * `local_connectivity::Integer = 1`: ローカルに接続されていると見なされるべき最近傍の数。値が高いほど、マニフォールドはより接続されます。これはマニフォールドの内因次元よりも高く設定すべきではありません。
  * `repulsion_strength::Real = 1`: 最適化プロセス中の負のサンプルの重み付け。
  * `neg_sample_rate::Integer = 5`: 各正のサンプルに対して選択する負のサンプルの数。高い値は計算コストを増加させますが、わずかに精度が向上します。
  * `tol::Real = 1e-4`: 埋め込みを最適化する際の早期停止の許容範囲。
  * `minbatch=0`: 並列計算がどのように行われるかを制御します。[`SimilaritySearch.getminbatch`](@ref) と `@batch`（`Polyester` パッケージ）を参照してください。
