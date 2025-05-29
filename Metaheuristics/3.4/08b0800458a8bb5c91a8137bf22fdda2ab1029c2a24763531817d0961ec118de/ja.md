```
Options(;
    x_tol::Real = 1e-8,
    f_tol::Real = 1e-12,
    f_tol_rel::Real = eps(),
    f_tol_abs::Real = 0.0,
    g_tol::Real = 0.0,
    h_tol::Real = 0.0,
    f_calls_limit::Real = 0,
    time_limit::Real = Inf,
    iterations::Int = 1,
    store_convergence::Bool = false,
    debug::Bool = false,
    seed = rand(UInt),
    rng  = default_rng_mh(seed),
    parallel_evaluation = false,
    verbose = false,
)

`Options` は、最大反復回数、デバッグオプション、最大関数評価回数など、メタヒューリスティクスの一般的な設定を保存します。

主なプロパティ：

  * `x_tol` は、`Information` に指定された場合の真の最小化者に対する許容誤差です。
  * `f_tol` は、`Information` に指定された場合の真の最小値に対する許容誤差です。
  * `f_tol_rel` は、相対的な許容誤差です。
  * `f_calls_limit` は、最大関数評価回数の制限です。
  * `time_limit` は、`optimize` が秒単位で費やすことができる最大時間です。
  * `iterations` は、許可される最大反復回数です。
  * `store_convergence` が `true` の場合、各世代/反復で現在の `State` を `State.convergence` にプッシュします。
  * `debug` が `true` の場合、`optimize` 関数は各反復の現在の `State`（および関心のある情報）を報告します。
  * `seed` は、乱数生成器のシード用の非負整数です。
  * `parallel_evaluation` は、バッチ評価を有効にします。
  * `verbose` は、各反復の簡略化された結果を表示します。
  * `rng` は、ユーザー定義の乱数生成器です。

# 例

```

julia-repl julia> options = Options(f*calls*limit = 1000, debug=false, seed=1);

julia> f(x) = sum(x.^2) f (generic function with 1 method)

julia> bounds = [  -10.0 -10 -10; # 下限                     10.0  10 10 ] # 上限 2×3 Array{Float64,2}:  -10.0  -10.0  -10.0   10.0   10.0   10.0

julia> state = optimize(f, bounds, ECA(options=options)); ```
