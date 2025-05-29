```
fit(::Type{NetworkLearnerObs}, X, y, Adj, fl_train, fl_exec, fr_train, fr_exec [;kwargs])
```

観察に基づくネットワーク学習フレームワークのトレーニングメソッド。

# 引数

  * `X::AbstractMatrix` トレーニングデータ（`fl_train`、`fl_exec`で使用; `use_local_data==true`の場合、`fr_train`でも使用される）
  * `Y::AbstractAray` データターゲット（`fl_train`、`fr_train`で使用）
  * `Adj::Vector{AbstractAdjacency}` 観察関係構造を含むベクトル（隣接オブジェクト）
  * `fl_train` ローカルモデルトレーニング「関数」; `fl_train((X,y))`の呼び出しをサポートするものであれば何でも可
  * `fl_exec` ローカルモデル予測「関数」; `Ml = fl_train((X,y))`の呼び出しをサポートするものであれば何でも可
  * `fr_train` 関係モデルトレーニング「関数」; `fr_train((Xr,y))`の呼び出しをサポートするものであれば何でも可
  * `fr_exec` 関係モデル予測「関数」; `Mr = fr_train((Xr,y))`の呼び出しをサポートするものであれば何でも可

`Xr`は、ローカルモデル予測関数と隣接構造の結果を使用して関係学習者によって生成された関係変数のデータセットです。

# キーワード引数

  * `priors::Vector{Float64}` クラスの事前分布（該当する場合）
  * `learner::Symbol` 関係学習者（すなわち変数生成器）；利用可能なオプション `:rn`, `:wrn`, `:bayesrn` および `:cdrn`（デフォルト `:wrn`）
  * `inference::Symbol` 集合推論メソッド；利用可能なオプション `:rl`, `:ic` および `:gs`（デフォルト `:rl`）
  * `normalize::Bool` 観察ごとに関係変数をL1ノルムに正規化するかどうか（デフォルト `true`）
  * `use_local_data::Bool` 関係モデルが提供されたローカルデータ（すなわち `X`）を使用するかどうか（デフォルト `true`）
  * `f_targets::Function` ローカル/関係モデルによって生成された推定からターゲットを抽出する関数

（デフォルト `f_targets = x->MLDataPattern.targets(indmax,x)`）

  * `obsdim::Int` 観察次元（デフォルト `2`）
  * `tol::Float64` 集合推論収束のための最大許容平均推定誤差（デフォルト `1e-6`）
  * `κ::Float64` リラクゼーションラベリングの開始定数、`learner == :rl`の場合に使用（デフォルト `1.0`）
  * `α::Float64` リラクゼーションラベリングの減衰定数、`learner == :rl`の場合に使用（デフォルト `0.99`）
  * `maxiter::Int` 集合推論の最大反復回数（デフォルト `100`）
  * `bratio::Float64` ギブスサンプリングのバンインに使用される反復の割合、すなわち `maxiter`（デフォルト `0.1`）
