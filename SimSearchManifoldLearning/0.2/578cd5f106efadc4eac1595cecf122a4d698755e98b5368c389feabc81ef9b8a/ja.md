```
fit(UMAP::UMAP, maxoutdim; <kwargs>)
```

以前に計算されたモデルを異なるコンポーネント数で再利用します

# キーワード引数

  * `n_epochs=50`: 実行するエポック数
  * `learning_rate::Real = 1f0`: 初期学習率
  * `learning_rate_decay::Real = 0.9f0`: エポックごとに学習率が調整される方法 `learning_rate *= learning_rate_decay`
  * `repulsion_strength::Float32 = 1f0`: 反発力（負のサンプリング用）
  * `neg_sample_rate::Integer = 5`: オブジェクトごとに使用される負の例の数。
  * `tol::Real = 1e-4`: 埋め込みを最適化する際の早期停止のための許容誤差。
  * `minbatch=0`: 並列計算がどのように行われるかを制御します。 [`SimilaritySearch.getminbatch`](@ref) および `@batch`（`Polyester`パッケージ）を参照してください。
