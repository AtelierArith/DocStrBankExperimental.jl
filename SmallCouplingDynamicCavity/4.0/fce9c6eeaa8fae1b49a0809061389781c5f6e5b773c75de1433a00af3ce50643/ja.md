```
run_SCDC(
    model::EpidemicModel{TI,TG},
    obsprob::Function,
    γ::Float64,
    maxiter::Int64,
    epsconv::Float64,
    damp::Float64;
    μ_cutoff::Float64 = -Inf,
    n_iter_nc::Int64 = 1,
    damp_nc::Float64 = 0.0,
    callback::Function=(x...) -> nothing,
    printlog::Bool = false,
    rng::AbstractRNG=Xoshiro(1234)) where {TI<:InfectionModel,TG<:Union{<:AbstractGraph,Vector{<:AbstractGraph}}}
```

小結合動的キャビティ（SCDC）推論アルゴリズムを実行します。

この関数は、指定された疫病モデルに対してSCDC推論を実行し、提供された証拠（尤度）確率関数や、患者ゼロである確率、最大反復回数、収束閾値、減衰係数などの他のパラメータを使用します。収束するまで、または最大反復回数に達するまで、キャビティメッセージを反復的に更新します。

# 引数

  * `model`: 疫病モデルを表す[`EpidemicModel`](@ref)。
  * `obsprob`: 植え付けられた状態xに対する観測Oの証拠（尤度）確率p(O|x)を表す関数。
  * `γ`: 患者ゼロである確率。
  * `maxiter`: 最大反復回数。
  * `epsconv`: アルゴリズムの収束閾値。
  * `damp`: アルゴリズムの減衰係数。

# キーワード引数

  * `μ_cutoff::Float64`: パラメータμのカットオフ値（デフォルトは-Inf）。
  * `n_iter_nc::Int64`: 非収束ケースの反復回数（デフォルトは1）。
  * `damp_nc::Float64`: 非収束ケースの減衰係数（デフォルトは0.0）。
  * `callback::Function`: 反復中に呼び出されるコールバック関数（デフォルトは何もしない）。
  * `printlog::Bool`: アルゴリズム中にログメッセージを印刷する（デフォルトはfalse）。
  * `rng::AbstractRNG`: 擬似乱数生成器（デフォルトはXoshiro）。

# 戻り値

  * `nodes`: 推論後の更新されたノード状態を表す[`Node`](@ref)オブジェクトの配列。

```
