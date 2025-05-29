```
run_SCDC!(
    nodes::Vector{Node{TI,TG}}, 
    model::EpidemicModel{TI,TG}, 
    γ::Float64, 
    maxiter::Vector{Int64}, 
    epsconv::Float64, 
    damp::Vector{Float64}; 
    μ_cutoff::Float64 = -Inf, 
    n_iter_nc::Int64 = 1, 
    damp_nc::Float64 = 0.0, 
    callback::Function=(x...) -> nothing,
    printlog::Bool = false,
    rng::AbstractRNG=Xoshiro(1234))
```

疫病モデルのためのSCDCアルゴリズムを実行します。このアルゴリズムは、ノードの現在の状態からメッセージパッシングの反復を再開します。

この関数は、指定された疫病モデルに対してSCDC推論を行い、提供された証拠（尤度）確率関数や、患者ゼロである確率、最大反復回数、収束閾値、減衰係数などの他のパラメータを使用します。収束するまで、または最大反復回数に達するまで、キャビティメッセージを反復的に更新します。減衰係数のためのダンピングスケジュールを実装しており、`maxiter`および`damp`引数で指定された特定の反復回数の後に減衰係数が変更されます。

# 引数

  * `nodes::Vector{Node{TI,TG}}`: 疫病モデル内のノードのベクター。
  * `model::EpidemicModel{TI,TG}`: 使用する疫病モデル。
  * `γ::Float64`: アルゴリズムのパラメータ（例：感染率）。
  * `maxiter::Vector{Int64}`: アルゴリズムの最大反復回数。
  * `epsconv::Float64`: アルゴリズムの収束閾値。
  * `damp::Vector{Float64}`: アルゴリズムの減衰係数。

# キーワード引数

  * `μ_cutoff::Float64`: パラメータμのカットオフ値（デフォルトは-Inf）。
  * `n_iter_nc::Int64`: 非収束ケースの反復回数（デフォルトは1）。
  * `damp_nc::Float64`: 非収束ケースの減衰係数（デフォルトは0.0）。
  * `callback::Function`: 反復中に呼び出されるコールバック関数（デフォルトは何もしない）。
  * `printlog::Bool`: アルゴリズム中にログメッセージを印刷する（デフォルトはfalse）。
  * `rng::AbstractRNG`: 擬似乱数生成器（デフォルトはXoshiro）。
