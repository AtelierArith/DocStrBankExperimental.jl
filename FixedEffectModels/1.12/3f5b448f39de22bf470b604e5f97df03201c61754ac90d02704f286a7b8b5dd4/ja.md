高次元のカテゴリ変数 / 楽器変数を用いた線形モデルの推定

### 引数

  * `df`: テーブル
  * `FormulaTerm`: [`@formula`](@ref) を使用して作成された式
  * `CovarianceEstimator`: 分散共分散行列を計算するためのメソッド

### キーワード引数

  * `contrasts::Dict = Dict()` 各カテゴリ変数のコントラストコーディングのオプションの辞書。指定されていない変数は `DummyCoding` を持ちます。
  * `weights::Union{Nothing, Symbol}` 重みのための列を参照するシンボル
  * `save::Symbol`: 残差と最終的に推定された固定効果をデータフレームに保存すべきですか？ デフォルトは `:none` です。残差のみを保存するには `save = :residuals`、固定効果のみを保存するには `save = :fe`、両方を保存するには `save = :all` を使用します。一度保存されると、`residuals(m)` または `fe(m)` を使用してアクセスできます。ここで `m` は推定によって返されるオブジェクトです。返されるデータフレームは元のデータフレームと自動的に整列されます。
  * `method::Symbol`: メソッドのためのシンボル。デフォルトは :cpu です。代わりに、:CUDA または :Metal を使用します（この場合、FixedEffectModels をインポートする前にそれぞれのパッケージをインポートする必要があります）。
  * `nthreads::Integer` 推定に使用するスレッドの数。`method = :cpu` の場合、デフォルトは `Threads.nthreads()` です。それ以外の場合、デフォルトは 256 です。
  * `double_precision::Bool`: 平均を取る操作は Float64 を使用すべきですか？ `method =:cpu` の場合はデフォルトで true、`method = :CUDA` または `method = :Metal` の場合は false です。
  * `tol::Real` 許容誤差。デフォルトは 1e-6 です。
  * `maxiter::Integer = 10000`: 最大反復回数
  * `drop_singletons::Bool = true`: シングルトンを削除すべきですか？
  * `progress_bar::Bool = true`: 回帰はプログレスバーを表示すべきですか？
  * `first_stage::Bool = true`: 第一段階の F 統計量と p 値を計算すべきですか？
  * `subset::Union{Nothing, AbstractVector} = nothing`: 特定の行を選択します。

### 詳細

楽器変数を持つモデルは 2SLS を使用して推定されます。`reg` は、Kleibergen-Paap rk Wald F 統計量を計算することによって弱い楽器をテストします。これは、非 i.i.d. エラーに対する Cragg-Donald Wald F 統計量の一般化です。この統計量は、Stata コマンド `ivreg2` によって返されるものに似ています。

### 例

```julia
using RDatasets, FixedEffectModels
df = dataset("plm", "Cigar")
reg(df, @formula(Sales ~ NDI + fe(State) + fe(State)&Year))
reg(df, @formula(Sales ~ NDI + fe(State)*Year))
reg(df, @formula(Sales ~ (Price ~ Pimin)))
reg(df, @formula(Sales ~ NDI), Vcov.robust())
reg(df, @formula(Sales ~ NDI), Vcov.cluster(:State))
reg(df, @formula(Sales ~ NDI), Vcov.cluster(:State , :Year))
df.YearC = categorical(df.Year)
reg(df, @formula(Sales ~ YearC), contrasts = Dict(:YearC => DummyCoding(base = 80)))
```

### エイリアス

`reg` は、より一般的な StatsAPI の `fit` のエイリアスです。

```julia
using RDatasets, FixedEffectModels
df = dataset("plm", "Cigar")
fit(FixedEffectModel, @formula(Sales ~ NDI + fe(State) + fe(State)&Year), df)
```
