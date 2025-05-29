```
fit(::Type{NetworkLearnerEnt}, X, update, Adj, fl_train, fl_exec, fr_train, fr_exec [;kwargs])
```

エンティティベースのネットワーク学習フレームワークのトレーニングメソッド。

# 引数

  * `Xo::AbstractMatrix` エンティティの初期推定値
  * `update::BitVector` 推定値が更新可能かどうかを示すマスク（`true` 値）またはそうでないか（`false` 値）；一般に、false 値はトレーニングサンプルの推定値に関連付けられます
  * `Adj::Vector{AbstractAdjacency}` エンティティの関係構造（隣接オブジェクト）を含むベクター
  * `fr_train` 関係モデルのトレーニング `function`；`fr_train((Xr,y))` の呼び出しをサポートするものであれば何でも可能です。ここで `y = f_targets(Xo)`
  * `fr_exec` 関係モデルの予測 `function`；`fr_exec(Mr,Xr)` の呼び出しをサポートするものであれば何でも可能です。ここで `Mr = fr_train((Xr,y))`

および `Xr` は、推定値 `Xo` と隣接構造を使用して関係学習者によって生成された関係変数のデータセットです。

# キーワード引数

  * `priors::Vector{Float64}` クラスの事前分布（該当する場合）
  * `learner::Symbol` 関係学習者（すなわち変数生成器）；利用可能なオプションは `:rn`, `:wrn`, `:bayesrn` および `:cdrn`（デフォルトは `:wrn`）
  * `inference::Symbol` 集合的推論メソッド；利用可能なオプションは `:rl`, `:ic` および `:gs`（デフォルトは `:rl`）
  * `normalize::Bool` エンティティごとに関係変数を L1 ノルムに正規化するかどうか（デフォルトは `true`）
  * `f_targets::Function` ローカル/関係モデルによって生成された推定値からターゲットを抽出する関数

（デフォルト `f_targets = x->MLDataPattern.targets(indmax,x)`）

  * `obsdim::Int` 観測次元（デフォルトは `2`）
  * `tol::Float64` 集合的推論収束のための最大許容平均推定誤差（デフォルトは `1e-6`）
  * `κ::Float64` リラクゼーションラベリングの開始定数、`learner == :rl` の場合に使用（デフォルトは `1.0`）
  * `α::Float64` リラクゼーションラベリングの減衰定数、`learner == :rl` の場合に使用（デフォルトは `0.99`）
  * `maxiter::Int` 集合的推論の最大反復回数（デフォルトは `100`）
  * `bratio::Float64` ギブスサンプリングのバンインに使用される反復の割合、すなわち `maxiter`（デフォルトは `0.1`）
