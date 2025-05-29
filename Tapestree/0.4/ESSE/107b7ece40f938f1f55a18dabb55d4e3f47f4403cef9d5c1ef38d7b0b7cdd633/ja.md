```
esse(tree_file   ::String,
     out_file    ::String,
     h           ::Int64;
     states_file ::String            = "NaN",
     envdata_file::String            = "NaN",
     cov_mod     ::NTuple{M,String}  = ("",),
     node_ps     ::Tuple{Bool,Int64} = (true, 10),
     out_states  ::String            = "",
     constraints ::NTuple{N,String}  = (" ",),
     mvpars      ::NTuple{O,String}  = (" ",),
     niter       ::Int64             = 10_000,
     nthin       ::Int64             = 10,
     nburn       ::Int64             = 200,
     tune_int    ::Int64             = 100,
     nswap       ::Int64             = 10,
     ncch        ::Int64             = 1,
     parallel    ::Bool              = ncch > 1,
     dt           ::Float64          = 0.2,
     ntakew      ::Int64             = 100,
     winit       ::Float64           = 2.0,
     scale_y     ::NTuple{2,Bool}    = (true, false),
     algorithm   ::String            = "pruning",
     mc          ::String            = "slice",
     λpriors     ::Float64           = .1,
     μpriors     ::Float64           = .1,
     gpriors     ::Float64           = .1,
     lpriors     ::Float64           = .1,
     qpriors     ::Float64           = .1,
     βpriors     ::NTuple{2,Float64} = (0.0, 10.0),
     hpriors     ::Float64           = .1,
     optimal_w   ::Float64           = 0.8,
     tni         ::Float64           = 1.0,
     obj_ar      ::Float64           = 0.6,
     screen_print::Int64             = 5,
     Eδt         ::Float64           = 1e-3,
     ti          ::Float64           = 0.0,
     ρ           ::Array{Float64,1}  = [1.0]) where {M,N,O}
```

地理的な **esse** を実行します。これらのファイルがどのように指定されるべきかについてはチュートリアルを参照してください。

# 引数

  * `tree_file::String`: 木ファイルへのフルパス。
  * `out_file::String`: MCMC出力を書き込むためのフルパス。
  * `h::Int64`: 隠れ状態の数。
  * `states_file ::String = "NaN"`: 状態ファイルへのフルパス。`"NaN"`の場合、観測された状態は使用されません（隠れ状態のみ）。
  * `envdata_file::String = "NaN"`: 共変量ファイルへのフルパス。`"NaN"`の場合、共変量は使用されません（すなわち、定数レート）。
  * `cov_mod::NTuple{M,String} = ("",)`: 共変量の影響を受けるレートを指定します：`s`は種分化、`e`は絶滅、`g`はコロニゼーション。1つ以上可能です。
  * `node_ps::Tuple{Bool,Int64} = (true, 10)`: 最初のインデックスはノードの事後周辺確率を計算するかどうかを指定し、2番目のインデックスは計算する反復の数です。
  * `out_states::String = ""`: ノード確率出力を書き込むためのフルパス。
  * `constraints::NTuple{N,String} = (" ",)`: モデルパラメータの制約。
  * `mvpars::NTuple{O,String} = (" ",)`: スライスサンプリングを使用して収束を改善するために多変量であるべきパラメータ。
  * `niter::Int64 = 10_000`: 反復の数。
  * `nthin::Int64 = 10`: MCMC状態を記録する頻度。
  * `nburn::Int64 = 200`: バーンインとして破棄する反復の数。
  * `tune_int::Int64 = 100`: MHの提案ウィンドウを調整するための`nburn`中の反復の数。
  * `nswap::Int64 = 10`: 各反復でMC3のチェーンの尤度を入れ替えようとします。
  * `ncch::Int64 = 1`: チェーンの数。
  * `parallel::Bool = false`: 並列実行するかどうか。
  * `dt::Float64 = 0.2`: MC3の温度。
  * `ntakew::Int64 = 100`: スライスサンプリングのウィンドウを調整するための`nburn`からの反復の数。
  * `winit::Float64 = 2.0`: スライスサンプリングの初期ウィンドウ。
  * `scale_y::NTuple{2,Bool} = (true, false)`: 最初のインデックスは共変量`y`を[0,1]にスケールするかどうか、2番目は共変量`y`を全体として[0,1]の間でスケールするかどうか。
  * `algorithm::String = "pruning"`: `pruning`（推奨）または`flow`の間の尤度アルゴリズム。
  * `mc::String = "slice"`: サンプリングの種類 `slice`（スライスサンプリング）または`mh`（メトロポリス・ヘイスティング）。
  * `λpriors::Float64 = 0.1`: 種分化のための指数事前のレート。
  * `μpriors::Float64 = 0.1`: グローバル絶滅のための指数事前のレート。
  * `gpriors::Float64 = 0.1`: コロニゼーションのための指数事前のレート。
  * `lpriors::Float64 = 0.1`: ローカル絶滅のための指数事前のレート。
  * `qpriors::Float64 = 0.1`: 隠れ状態遷移のための指数事前のレート。
  * `βpriors::NTuple{2,Float64} = (0.0, 10.0)`: 共変量の効果のための正規事前の平均と分散。
  * `hpriors::Float64 = 0.1`: 隠れ状態間の違いのための指数事前のレート。
  * `optimal_w::Float64 = 0.8`: 最適ウィンドウ。
  * `tni::Float64 = 1.0`: レートの初期調整。
  * `obj_ar::Float64 = 0.23`: 目的の受け入れ率。
  * `screen_print::Int64 = 5`: スクリーンログを更新するまでの待機秒数。
  * `Eδt::Float64 = 1e-3`: フローアルゴリズム用。
  * `ti::Float64 = 0.0`: フローアルゴリズム用。
  * `ρ::Array{Float64,1} = [1.0]`: 各状態（各領域および広範囲）のサンプリング割合。

# 戻り値

  * mcmcパラメータの配列。
