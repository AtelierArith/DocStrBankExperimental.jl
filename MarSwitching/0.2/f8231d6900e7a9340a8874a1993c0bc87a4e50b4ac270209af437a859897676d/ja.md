```
grid_search_msm(y::VecOrMat{V}, 
                x::VecOrMat{V},
                criterion::String = "AIC";
                k::Vector{Int64} = [2,3,4],
                intercept::Vector{String} = ["switching", "non-switching"],
                vars::Vector{Vector{String}},
                switching_var::Vector{Bool} = [true, false],
                random_n::Int64,
                random_search_em::Int64 = 0,
                random_search::Int64 = 0,
                verbose::Bool = true,
                algorithm::Symbol = :LN_SBPLX,
                maxtime::Int64 = -1) where V <: AbstractFloat
```

指定されたパラメータ値に対するマルコフスイッチングモデル（現在は非TVTP）のための徹底的またはランダムな探索のための関数です。

選択されたMSMモデル、基準値のベクトル、およびパラメータ空間を含むタプルのベクトルを返します。

注意: データのサイズが小さい場合（両方の次元）、パラメータ空間を制限するために、より小さな可能なパラメータを提供するか、評価するパラメータのランダムな数を選択することをお勧めします。

# 引数

  * `y::VecOrMat{V}`: 従属変数。
  * `x::VecOrMat{V}`: 独立変数。
  * `criterion::String`: モデル選択に使用する基準。 "AIC"（デフォルト）または "BIC" のいずれか。
  * `k::Int64`: 評価する状態のベクトル。
  * `intercept::String`: "switching"、"non-switching" または "no" のベクトル。
  * `vars::Vector{Vector{String}}`: `x` 引数の対応する変数に対して "switching" または "non-switching" のいずれかを持つベクトルのベクトル。
  * `switching_var::Vector{Bool}`: 分散状態依存性のためのブール値のベクトル。
  * `switching_var::Bool`: 分散状態は依存していますか？
  * `random_n::Int64`: 評価するランダムなパラメータの組み合わせの数。負の場合、徹底的なグリッド検索を実行します。
  * `random_search_em::Int64`: 各モデル推定におけるEMアルゴリズムのために実行するランダム検索の数。0の場合、ランダム検索は実行されません。
  * `random_search::Int64`: 実行するランダム検索の数。
  * `algorithm::Symbol`: 使用する最適化アルゴリズム。[:LD*VAR2, :LD*VAR1, :LD*LBFGS, :LN*SBPLX] のいずれか。
  * `maxtime::Int64`: 最適化を実行する最大時間（秒）。負の場合、最大時間は T/2 に等しくなります。
  * `verbose::Bool`: true の場合、グリッド/ランダム検索の進行状況を出力します。

詳細は [`MSModel`](@ref) を参照してください。
