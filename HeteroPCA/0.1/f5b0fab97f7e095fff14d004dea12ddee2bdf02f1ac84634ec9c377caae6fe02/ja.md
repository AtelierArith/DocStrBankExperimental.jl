```
heteropca(X, rank=size(X, 1); kwargs...)
```

`fit(HeteroPCAModel, X, rank=size(X, 1); kwargs...)` の便利なラッパーです。

# 引数

  * `X::AbstractMatrix{T}`: 次元 `d × n` の入力データ行列
  * `rank::Int=size(X, 1)`: 目標次元 *k* （抽出する成分の数）

# キーワード引数

  * `maxiter::Int=1_000`: アルゴリズムの最大反復回数
  * `abstol::Float64=1e-6`: 対角推定の収束許容範囲
  * `demean::Bool=true`: 列の平均を引いてデータを中心化するかどうか; モデルがすでに中心化されている場合は `demean=false` に設定
  * `impute_method::Symbol=:pairwise`: 欠損値を処理する方法 (:pairwise または :zero); `impute = :pairwise` は利用可能なデータのみを使用してペアワイズ共分散行列を計算; `impute = :zero` は中心化後に欠損値をゼロで埋め、サンプルの欠損率に調整された共分散行列を計算します。
  * `alpha::Float64=1.0`: 対角更新の緩和パラメータ; `alpha = 1` は元のスキームを再現します;
