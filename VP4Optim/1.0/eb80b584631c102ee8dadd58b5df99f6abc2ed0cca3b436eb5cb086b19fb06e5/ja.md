```
check_model(pars, vals, c_, data_;
what=(:consistency, :derivatives, :optimization),
small=sqrt(eps()),
x0=[], lx=[], ux=[], x_scale=[],
precon=true,
visual=false,
rng=MersenneTwister(),
Hessian=true,
log10_rng=range(-6, -3, 10),
min_slope=0.9)
```

特定のモデルが通過すべきテスト。

# 引数

  * `pars::ModPar{T}`: コンストラクタ `create_model(pars)` のためのモデルパラメータ。
  * `vals::Vector{Float64}`: モデルが依存する*すべての*非線形パラメータ。`Model` フィールド `val` で定義されているように。
  * `c_::Vector{Nc, T}`: モデルが依存する線形係数。
  * `data_::AbstractArray`: *真の*パラメータ `vals` と `c_` に対応するデータで、`set_data!` に適した形式。
  * `what::Tuple{Symbol}`: 実行されるテスト (以下を参照)。
  * `small::Float64`: 精度基準として必要。
  * `x0::Vector{Float64}`: 最適化のための出発点および導関数がテストされる位置。
  * `lx::Vector{Float64}`: 最適化の下限
  * `ux::Vector{Float64}`: 最適化の上限
  * `x_scale::Vector{Float64}`: スケーリングベクトル、`δx = randn(size(x)) .* x_scale` が合理的になるように。
  * `precon::Bool`: 前処理器の有無で最適化をテスト。
  * `visual::Bool`: `true` の場合、導関数テストのための二重対数プロットも生成。
  * `rng::MersenneTwister`: 再現可能なテストのためにユニークなシード (例: `MersenneTwister(42)`) を渡すことを許可。
  * `Hessian::Bool`: モデルが二次導関数を実装していない場合は `false` に設定するべき。
  * `log10_rng::AbstractVector`: 導関数テストのための対数範囲
  * `min_slope::Float64`: 対数-対数プロット上の最小導関数傾斜

## 注記

  * テストはすべての `x_sym ⊆ sym` に対して実行される。
  * テスト結果に関する詳細情報を持つ辞書を返す。
  * `:consistency ∈ what`: いくつかの基本テスト (パラメータ、名前、正しいモデル値)
  * `:derivatives ∈ what`: `x0` での一次および二次偏導関数をチェック。
  * `:optimization ∈ what`: `x0` を出発点とし、`lx` と `ux` を境界としてモデルを最小化。
  * 例のアプリケーションは [`test_BiExpDecay.jl`](https://github.com/cganter/VP4Optim.jl/blob/main/test/test_BiExpDecay.jl) に見つけることができます。これは、自分のモデルでテストを実行する方法のテンプレートとしても機能するはずです。
