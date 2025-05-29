```
fit(Type{UMAP}, knns, dists; <kwargs>) -> UMAPオブジェクト
```

データ `(X, dist)` を `maxoutdim` 次元空間に埋め込むモデルを作成します。`knns` と `dists` は共同で $(X, dist)$ のすべての `k` 最近傍を指定し、これらの結果には自己参照を含めてはいけません。`SimilaritySearch` の `allknn` メソッドを参照してください。

# 引数

  * `knns`: 整数 (識別子) の $(k, n)$ 行列。
  * `dists`: 浮動小数点 (距離) の $(k, n)$ 行列。

プロジェクションには利用可能なすべてのスレッドを使用します。

# キーワード引数

  * `maxoutdim::Integer=2`: 埋め込みのコンポーネント数
  * `n_epochs::Integer = 300`: 埋め込み最適化のためのトレーニングエポック数
  * `learning_rate::Real = 1`: 最適化中の初期学習率
  * `learning_rate_decay::Real = 0.9`: 各エポックで `learning_rate` がどのように更新されるか `(learning_rate *= learning_rate_decay)` (最小値は 1e-6 として考慮されます)
  * `layout::AbstractLayout = SpectralLayout()`: 出力埋め込みの初期化方法
  * `min_dist::Real = 0.1`: 出力埋め込み内の点の最小間隔
  * `spread::Real = 1`: 埋め込まれた点の効果的なスケール。`min_dist` と組み合わせて埋め込まれた点がどれだけクラスタ化されるかを決定します。
  * `set_operation_ratio::Real = 1`: UMAPグラフを構築する際にファジー集合の和とファジー集合の交差の間を補間します (グローバルファジー単体集合)。このパラメータの値は 1.0 と 0.0 の間である必要があります: 1.0 は純粋なファジー和を示し、0.0 は純粋なファジー交差を示します。
  * `local_connectivity::Integer = 1`: ローカルに接続されていると見なされるべき最近傍の数。値が高いほど、マニフォールドはより接続されます。この値はマニフォールドの内因次元よりも高く設定すべきではありません。
  * `repulsion_strength::Real = 1`: 最適化プロセス中の負のサンプルの重み付け。
  * `neg_sample_rate::Integer = 5`: 各正のサンプルに対して選択する負のサンプルの数。値が高いほど計算コストが増加しますが、わずかに精度が向上します。
  * `tol::Real = 1e-4`: 埋め込みを最適化する際の早期停止に対する許容誤差。
  * `minbatch=0`: 並列計算の方法を制御します。ゼロは `SimilaritySearch` のデフォルトを使用し、-1 は並列計算を避けます; `Polyester` パッケージの `@batch` マクロに渡されます。
  * `a = nothing`: これは埋め込みを制御します。デフォルトでは、`min_dist` と `spread` によって自動的に決定されます。
  * `b = nothing`: これは埋め込みを制御します。デフォルトでは、`min_dist` と `spread` によって自動的に決定されます。
