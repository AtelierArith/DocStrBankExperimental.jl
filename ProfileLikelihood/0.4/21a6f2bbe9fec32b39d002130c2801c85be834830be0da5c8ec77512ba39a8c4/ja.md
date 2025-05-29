```
profile(prob::LikelihoodProblem, sol::LikelihoodSolution, n=1:number_of_parameters(prob);
    alg=get_optimiser(sol),
    conf_level::F=0.95,
    confidence_interval_method=:spline,
    threshold=get_chisq_threshold(conf_level),
    resolution=200,
    param_ranges=construct_profile_ranges(sol, get_lower_bounds(prob), get_upper_bounds(prob), resolution),
    min_steps=10,
    normalise::Bool=true,
    spline_alg=FritschCarlsonMonotonicInterpolation,
    extrap=Line,
    parallel=false,
    next_initial_estimate_method = :prev,
    kwargs...)
```

尤度問題 `prob` からのパラメータのプロファイル尤度を MLE `sol` を用いて計算します。

結果に満足できない場合は、パラメータを再プロファイルするための [`replace_profile!`](@ref) も参照してください。プロットについては、`plot_profiles` 関数を参照してください（Makie.jl のバックエンドをロードしている必要があります）。

# 引数

  * `prob::LikelihoodProblem`: [`LikelihoodProblem`](@ref)。
  * `sol::LikelihoodSolution`: [`LikelihoodSolution`](@ref)。さらに [`mle`](@ref) も参照してください。
  * `n=1:number_of_parameters(prob)`: プロファイル尤度を計算するためのパラメータインデックス。

# キーワード引数

  * `alg=get_optimiser(sol)`: 各最適化問題を解決するために使用する最適化アルゴリズム。
  * `conf_level::F=0.95`: [`ConfidenceInterval`](@ref) に使用するレベル。
  * `confidence_interval_method=:spline`: 信頼区間を計算するために使用する方法。さらに [`get_confidence_intervals!`](@ref) も参照してください。デフォルトの `:spline` はデータを通るスプラインのルートファインディングを使用し、連続関数を定義します。一方、代替の `:extrema` はしきい値を超える値の極値を単に取ります。
  * `threshold=get_chisq_threshold(conf_level)`: 信頼区間を定義するために使用するしきい値。
  * `resolution=200`: MLE から始まる各方向でプロファイル尤度を評価するために使用するポイントの数（合計で `2resolution` ポイント）。 - `resolution=200`: 以下の `grids` を定義するために使用するポイントの数で、各関心パラメータの左と右のポイントの数を示します。これはベクトルでも可能で、例えば `resolution = [20, 50, 60]` は最初のパラメータに `20` ポイント、2 番目に `50`、3 番目に `60` ポイントを使用します。
  * `param_ranges=construct_profile_ranges(sol, get_lower_bounds(prob), get_upper_bounds(prob), resolution)`: 各パラメータに使用する範囲。
  * `min_steps=10`: 各方向でプロファイルを許可する最小ステップ数。しきい値に達する前にこの数未満のステップが使用された場合、アルゴリズムは再起動し、その方向で `min_steps` のポイント数のプロファイル尤度を計算します。さらに `min_steps_fallback` も参照してください。
  * `min_steps_fallback=:replace`: 最小ステップ数 `min_steps` に達しない場合にプロファイルを更新するために使用する方法。さらに [`reach_min_steps!`](@ref) も参照してください。`:replace` の場合、プロファイルは完全に置き換えられ、`min_steps` の等間隔のポイントを使用して置き換えます。`:refine` の場合、グリッド内の一部のスペースを埋めて `min_steps` のポイント数に達します。この後者のオプションは、パラメータ値間の間隔がもはや一定でないことを意味します。`:refine_parallel` を使用して `:refine` を並行して適用できます。
  * `normalise::Bool=true`: 正規化されたプロファイル対数尤度を最適化するかどうか。
  * `spline_alg=FritschCarlsonMonotonicInterpolation`: プロファイルデータからスプラインを計算するために使用する補間アルゴリズム。Interpolations.jl を参照してください。
  * `extrap=Line`: プロファイルデータからスプラインを計算するために使用する外挿アルゴリズム。Interpolations.jl を参照してください。
  * `parallel=false`: マルチスレッドを使用するかどうか。`true` の場合、マルチスレッドを使用して複数のパラメータを同時にプロファイルし、左と右のステップを同時に行います。
  * `next_initial_estimate_method = :prev`: プロファイリング中に前進する際に次の初期推定を選択するための方法。`:prev` は単に前の解を使用しますが、`:interp` を使用して線形補間を使用することもできます。さらに [`set_next_initial_estimate!`](@ref) も参照してください。
  * `kwargs...`: `OptimizationProblem` を解決するために `solve` に渡す追加のキーワード引数。Optimization.jl のドキュメントも参照してください。

# 出力

[`ProfileLikelihoodSolution`](@ref) を返します。
