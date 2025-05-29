```
SurrogateTest(f::Function, x, method::Surrogate; kwargs...) → test
```

入力データ `x` のためのサロゲートテストを初期化します。これは [`pvalue`](@ref) で使用できます。このテストは、時系列（`x` のような）を与えられたときに実数を出力する関数 `f` と、サロゲートを生成する方法を入力として必要とします。`f` は識別統計量を計算する関数です。

[`pvalue`](@ref) で呼び出されると、`test` は識別統計量の実際の値 `rval` とサロゲート値 `vals` をそれぞれフィールド `rval, vals` に推定して保存します。p値を気にしない場合は、[`fill_surrogate_test!`](@ref) を直接使用することもできます。

`SurrogateTest` は、ドキュメントページ [Performing surrogate hypothesis tests](@ref) に記載されているプロセスを自動化します。

`SurrogateTest` は `HypothesisTest` のサブタイプであり、StatsAPI.jl インターフェースの一部です。

## キーワード

  * `rng = Random.default_rng()`: ランダム数生成器。
  * `n::Int = 10_000`: 生成して `f` を計算するサロゲートの数。
  * `threaded = true`: 利用可能なスレッド（`Threads.nthreads()`）でサロゲート計算のループを並列化するかどうか。
