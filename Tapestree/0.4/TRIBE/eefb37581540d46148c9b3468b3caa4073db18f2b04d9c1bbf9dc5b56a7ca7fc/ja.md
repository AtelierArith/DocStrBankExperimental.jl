```
tribe(tree_file   ::String,
      data_file   ::String,
      out_file    ::String;
      min_dt      ::Float64           = 0.01,
      niter       ::Int64             = 50_000,
      nburn       ::Int64             = 50_000,
      nthin       ::Int64             = 500,
      saveXY      ::Tuple{Bool,Int64} = (false, 1_000),
      saveDM      ::Tuple{Bool,Int64} = (false, 1_000),
      ωxprior     ::NTuple{2,Float64} = (0.,10.),
      ω1prior     ::NTuple{2,Float64} = (0.,10.),
      ω0prior     ::NTuple{2,Float64} = (0.,10.),
      σ²prior     ::Float64           = 1e-1,
      λprior      ::Float64           = 1e-1,
      weight      ::NTuple{5,Float64} = (0.15,0.05,0.02,0.02,5e-3),
      λ1i         ::Float64           = 1.0,
      λ0i         ::Float64           = 0.5,
      ωxi         ::Float64           = 0.0,
      ω1i         ::Float64           = 0.0,
      ω0i         ::Float64           = 0.0,
      fix_ωx      ::Bool              = false,
      fix_ω1      ::Bool              = false,
      fix_ω0      ::Bool              = false,
      delim       ::Char              = '	',
      eol         ::Char              = '',
      screen_print::Int64             = 5)
```

**tribe** モデルを実行します。

...

# 引数

  * `tree_file::String`: ツリーファイルへのフルパス。
  * `data_file::String`: データファイルへのフルパス。
  * `out_file::String`: MCMC出力を書き込むためのフルパス。
  * `min_dt::Float64 = 0.01`: 離散化のために許可されるツリーの高さの割合（値が低いほど精度が高いが、時間がかかる）。
  * `niter::Int64 = 50_000`: 繰り返しの回数。
  * `nburn::Int64 = 50_000`: 適応的バーンインフェーズの繰り返しの回数。
  * `nthin::Int64 = 500`: 繰り返しのサンプリング頻度。
  * `saveXY::Tuple{Bool,Int64} = (false, 1_000)`: データ拡張履歴を保存するかどうかの最初のインデックス、サンプリング頻度のための2番目のインデックス。
  * `saveDM::Tuple{Bool,Int64} = (false, 1_000)`: 長さ2のタプル：最初はデータ拡張された決定論的効果を保存するかどうかのブール値、2番目はサンプリング頻度の整数。
  * `ωxprior::NTuple{2,Float64} = (0.,10.)`: ωxの正規事前のための長さ2のタプル、最初は平均、2番目は分散。
  * `ω1prior::NTuple{2,Float64} = (0.,10.)`: ω1の正規事前のための長さ2のタプル、最初は平均、2番目は分散。
  * `ω0prior::NTuple{2,Float64} = (0.,10.)`: ω0の正規事前のための長さ2のタプル、最初は平均、2番目は分散。
  * `σ²prior::Float64 = 1e-1`: σ²の指数事前の平均のための浮動小数点数。
  * `λprior::Float64 = 1e-1`: 両方のλの指数事前の平均のための浮動小数点数。
  * `weight::NTuple{5,Float64} = (0.15,0.05,0.02,0.02,5e-3)`: σ²、ωx、ω1 & ω0、λ1 & λ0をそれぞれ更新するための確率を指定する長さ5のタプル。
  * `λ1i::Float64 = 1.0`: λ1の開始値のための浮動小数点数。
  * `λ0i::Float64 = 0.5`: λ0の開始値のための浮動小数点数。
  * `ωxi::Float64 = 0.0`: ωxの開始値のための浮動小数点数。
  * `ω1i::Float64 = 0.0`: ω1の開始値のための浮動小数点数。
  * `ω0i::Float64 = 0.0`: ω0の開始値のための浮動小数点数。
  * `fix_ωx::Bool = false`: ωxなしで推論を行うためのブール値。
  * `fix_ω1::Bool = false`: ω1なしで推論を行うためのブール値。
  * `fix_ω0::Bool = false`: ω0なしで推論を行うためのブール値。
  * `delim::Char= '	'`: ddlmのための。
  * `eol::Char= ' '`: ddlmのための。
  * `screen_print::Int64 = 5`: スクリーンログを更新するまでの待機秒数。

...

...

# 戻り値

  * mcmcパラメータの配列。

...
