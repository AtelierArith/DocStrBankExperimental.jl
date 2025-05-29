```
MSModel(y::VecOrMat{V},
        k::Int64, 
        ;intercept::String = "switching",
        exog_vars::VecOrMat{V},
        exog_switching_vars::VecOrMat{V},
        switching_var::Bool = true,
        exog_tvtp::VecOrMat{V},
        x0::Vector{V},
        algorithm::Symbol = :LN_SBPLX,
        maxtime::Int64 = -1,
        random_search::Int64 = 0,
        random_search_em::Int64,
        verbose::Bool) where V <: AbstractFloat
```

マルコフスイッチングモデルを推定するための関数。MSM構造体のインスタンスを返します。

注意: モデルの尤度関数は非常に非線形で、局所的な最大値に陥りやすいです。ランダムサーチの回数を増やすことで、トレーニング時間が長くなる代わりに改善される可能性があります。同じ理由から、状態数が多いモデル（例: 5以上）を推定しないことをお勧めしますが、可能ではあります。

# 引数

  * `y::VecOrMat{V}`: 従属変数。
  * `k::Int64`: 状態の数。
  * `intercept::String`: "switching" または "non-switching" または "no"。
  * `exog_vars::VecOrMat{V}`: モデルの非スイッチング部分のためのオプションの外生変数。
  * `exog_switching_vars::VecOrMat{V}`: モデルのスイッチング部分のためのオプションの外生変数。
  * `switching_var::Bool`: 分散は状態依存ですか？
  * `exog_tvtp::VecOrMat{V}`: モデルのtvtp部分のためのオプションの外生変数。
  * `x0::Vector{V}`: パラメータの初期推定値。空の場合、初期推定値はk-meansクラスタリングから生成されます。
  * `algorithm::Symbol`: 使用する最適化アルゴリズム。[`:LD_VAR2`, `:LD_VAR1`, `:LD_LBFGS`, `:LN_SBPLX`]のいずれか。
  * `maxtime::Int64`: 最適化を実行する最大時間（秒）。負の場合、最大時間はT/2に等しくなります。
  * `random_search_em::Int64`: EMアルゴリズムのために実行するランダムサーチの回数。0の場合、ランダムサーチは実行されません。
  * `random_search::Int64`: 実行するランダムサーチの回数。
  * `verbose::Bool`: trueの場合、ランダムサーチの進行状況を出力します。

参考文献:

  * Hamilton, J. D. (1989). A new approach to the economic analysis of nonstationary time series and the business cycle. Econometrica: Journal of the Econometric Society, 357-384.
  * Filardo, Andrew J. (1994). Business cycle phases and their transitional dynamics. Journal of Business & Economic Statistics, 12(3), 299-308.

他に[`grid_search_msm`](@ref)も参照してください。
