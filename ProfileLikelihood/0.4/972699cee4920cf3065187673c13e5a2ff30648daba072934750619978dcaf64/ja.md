```
bivariate_profile(prob::LikelihoodProblem, sol::LikelihoodSolution, n::NTuple{M,NTuple{2,Int}};
    alg=get_optimiser(sol),
    conf_level::F=0.95,
    confidence_region_method=Val(:contour),
    threshold=get_chisq_threshold(conf_level, 2),
    resolution=200,
    grids=construct_profile_grids(n, sol, get_lower_bounds(prob), get_upper_bounds(prob), resolution),
    min_layers=10,
    outer_layers=0,
    normalise=Val(true),
    parallel=Val(false),
    next_initial_estimate_method=Val(:nearest),
    kwargs...) where {M,F}
```

尤度問題 `prob` からのパラメータに対する二変量プロファイル尤度を計算します。MLE `sol` を使用してこの関数を呼び出すこともできます。また、`Symbols` を使用してこの関数を呼び出すこともできます。たとえば、`get_syms(prob) = [:λ, :K, :u₀]` の場合、`bivariate_profile(prob, sol, ((:λ, :K), (:K, u₀)))` を呼び出すことは、`bivariate_profile(prob, sol, ((1, 2), (2, 3)))` を呼び出すのと同じです（整数座標表現は、解の中で依然として使用されます）。

プロットについては、`plot_profiles` 関数を参照してください（Makie.jl のバックエンドをロードしている必要があります）。

# 引数

  * `prob::LikelihoodProblem`: [`LikelihoodProblem`](@ref)。
  * `sol::LikelihoodSolution`: [`LikelihoodSolution`](@ref)。また、[`mle`](@ref)も参照してください。
  * `n::NTuple{M,NTuple{2,Int}}`: プロファイル尤度を計算するためのパラメータインデックス。これらはインデックスのタプルである必要があります。たとえば、`n = ((1, 2),)` はパラメータ `1` と `2` の間の二変量プロファイルを計算します。

# キーワード引数

  * `alg=get_optimiser(sol)`: 各最適化問題を解決するために使用する最適化手法。
  * `conf_level::F=0.95`: [`ConfidenceRegion`](@ref) に使用するレベル。
  * `confidence_region_method=:contour`: 信頼領域を計算するために使用する方法。`get_confidence_regions!` も参照してください。デフォルトは `:contour` で、Contour.jl を使用して信頼領域の境界を計算します。代替オプションは `:delaunay` で、DelaunayTriangulation.jl と三角形の輪郭を使用して境界を見つけます。この後者のオプションは、すでに `using DelaunayTriangulation` を行っている場合にのみ利用可能です。
  * `threshold=get_chisq_threshold(conf_level, 2)`: 信頼領域を定義するために使用する閾値。
  * `resolution=200`: 下の `grids` を定義するために使用するポイントの数。これは、各関心パラメータの左と右にあるポイントの数を示します。これもベクトルにすることができ、たとえば `resolution = [20, 50, 60]` は最初のパラメータに `20` ポイント、2 番目に `50`、3 番目に `60` ポイントを使用します。値のペア間のグリッドを定義する際には、2 つの解像度の最大値が使用されます（したがって、正方形のグリッドが定義されます）。
  * `grids=construct_profile_grids(n, sol, get_lower_bounds(prob), get_upper_bounds(prob), resolution)`: 各パラメータペアに使用するグリッド。
  * `min_layers=10`: MLE から離れたプロファイルを許可する最小層数。閾値に達する前にこの層数未満が使用された場合、アルゴリズムは再起動し、その方向に `min_steps` ポイントのプロファイル尤度を計算します。
  * `outer_layers=0`: 信頼領域のバウンディングボックスから外に出る層の数。
  * `normalise=true`: 正規化されたプロファイル対数尤度を最適化するかどうか。
  * `parallel=false`: マルチスレッドを使用するかどうか。`true` の場合、マルチスレッドを使用して複数のパラメータを同時にプロファイルし、層内の各ノードでの解の評価にかかる作業を各スレッドに分配します。
  * `next_initial_estimate_method = :nearest`: プロファイリング時に次の層にステップする際に次の初期推定を選択する方法。`:nearest` は単に前の層から最も近いノードの解を使用しますが、`:mle` を使用して MLE を再利用することや、`:interp` を使用して線形補間を行うこともできます。[`set_next_initial_estimate!`](@ref) も参照してください。
  * `kwargs...`: `OptimizationProblem` を解決するために `solve` に渡す追加のキーワード引数。Optimization.jl のドキュメントも参照してください。

# 出力

[`BivariateProfileLikelihoodSolution`](@ref) を返します。 ```
